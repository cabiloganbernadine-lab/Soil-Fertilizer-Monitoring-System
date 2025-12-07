### Firebase Cloud Firestore Schema

#### 1. Users Collection

This collection stores information about the users of the system.

-   **Collection:** `users`
-   **Document ID:** `user_id` (auto-generated)

| Field        | Type      | Description                                |
| :----------- | :-------- | :----------------------------------------- |
| `name`       | `string`  | The user's full name.                      |
| `email`      | `string`  | The user's email address (for login).      |
| `password`   | `string`  | The user's hashed password.                |
| `role`       | `string`  | `admin` or `user`.                         |
| `created_at` | `timestamp` | The timestamp when the user account was created. |

#### 2. Devices Collection

This collection stores information about the IoT devices.

-   **Collection:** `devices`
-   **Document ID:** `device_id` (auto-generated)

| Field           | Type      | Description                                   |
| :-------------- | :-------- | :-------------------------------------------- |
| `device_name`   | `string`  | The name of the device (e.g., "Greenhouse Sensor"). |
| `location`      | `string`  | The location of the device.                   |
| `status`        | `string`  | `online` or `offline`.                        |
| `user_id`       | `string`  | The ID of the user who owns the device.       |
| `registered_at` | `timestamp` | The timestamp when the device was registered. |

#### 3. Soil_Data Collection

This collection stores the time-series data from the IoT devices.

-   **Collection:** `soil_data`
-   **Document ID:** `data_id` (auto-generated)

| Field          | Type      | Description                               |
| :------------- | :-------- | :---------------------------------------- |
| `device_id`    | `string`  | The ID of the device that sent the data.  |
| `moisture_level` | `number`  | The soil moisture level in %.             |
| `temperature`  | `number`  | The temperature in °C.                    |
| `humidity`     | `number`  | The humidity in %.                        |
| `timestamp`    | `timestamp` | The timestamp when the data was recorded. |

#### 4. Fertilizer_Recommendations Collection

This collection stores the fertilizer recommendations based on soil conditions.

-   **Collection:** `fertilizer_recommendations`
-   **Document ID:** `recommendation_id` (auto-generated)

| Field                   | Type     | Description                                     |
| :---------------------- | :------- | :---------------------------------------------- |
| `moisture_condition`    | `string` | `Low`, `Normal`, `High`.                        |
| `temperature_condition` | `string` | `Cold`, `Warm`, `Hot`.                          |
| `suggested_fertilizer`  | `string` | The name of the recommended fertilizer.         |
| `description`           | `string` | A description of the fertilizer and its benefits. |

#### 5. Logs / History Collection

This collection stores a historical record of all readings and analyses.

-   **Collection:** `logs`
-   **Document ID:** `log_id` (auto-generated)

| Field         | Type      | Description                                  |
| :------------ | :-------- | :------------------------------------------- |
| `data_id`     | `string`  | The ID of the soil data record.              |
| `device_id`   | `string`  | The ID of the device that sent the data.     |
| `user_id`     | `string`  | The ID of the user who owns the device.      |
| `date_logged` | `timestamp` | The timestamp when the log was created.      |
| `status`      | `string`  | `Analyzed`, `Pending`.                       |

#### 6. Notifications Collection

This collection stores notifications for users.

-   **Collection:** `notifications`
-   **Document ID:** `notification_id` (auto-generated)

| Field       | Type      | Description                               |
| :---------- | :-------- | :---------------------------------------- |
| `message`   | `string`  | The notification message.                 |
| `type`      | `string`  | `alert` or `info`.                        |
| `user_id`   | `string`  | The ID of the user who receives the notification. |
| `timestamp` | `timestamp` | The timestamp when the notification was created. |
| `status`    | `string`  | `read` or `unread`.                       |
