# Settings

## Application settings

### Snapshot interval

Defines how often a data snapshot of endpoints is taken. Can be overridden for individual endpoints in the endpoint configuration.

### Use custom logo

Replaces our logo with your own. Toggle on and enter the URL to the logo. The recommended size is 155px by 55px.

### Allow the collection of anonymous statistics

We collect anonymized information about your Portainer installation to help with our product development. You can opt out during installation, or toggle this setting off at any time. 

![](../../.gitbook/assets/settings-4.png)

### App Templates

You can deploy containers and services using Portainer's set of built-in app templates, or [replace them with your own](../../advanced/app-templates/build.md) set of templates. Once you have a JSON file containing the template definitions, you can provide the URL to it here.

![](../../.gitbook/assets/settings-5.png)

### Edge Compute

To enable [Edge Compute](../../user/edge/) functionality in Portainer, select **Settings** from the menu then scroll down to the **Edge Compute** section. Toggle **Enable edge compute features** on then click **Save settings**. You can also adjust the **Edge agent default poll frequency** of individual endpoints to a value that suits.

![](../../.gitbook/assets/be-settings-edge-compute-1.gif)

Once Edge Compute is enabled, more options will be available in the menu:

![](../../.gitbook/assets/be-settings-edge-compute-2.png)

## Hidden containers

Stops a container from appearing in the Portainer UI through the container label. Enter the name and value of the label, then click **Add filter**. Containers with matching labels will be hidden.

![](../../.gitbook/assets/settings-3.png)

## Backup Portainer

This setting contains all of the information that Portainer stores on the `/data` volume, archived in a `tar.gz` file, and is optionally encrypted with a password. This archive is all you need to restore Portainer.

### Backing up to a local disk <a id="backup-to-local-disk"></a>

Log in as an admin user. From the menu select **Settings**, then scroll down to the **Backup Portainer** section.

![](../../.gitbook/assets/be-settings-backup-1.gif)

**Download backup file** is the default option. As an optional step, toggle **Password protect** on and enter a password to encrypt the backup file. When you click **Download backup**, a `tar.gz` file will be downloaded via the browser.

### Backing up to S3

With Portainer Business Edition you have the option to store a backup of your configuration in an S3 bucket, either on demand or on a defined schedule.

To do this, log in as an admin user, select **Settings** from the menu, then scroll down to **Backup Portainer**. Select **Store in S3** and fill in the options, using the below as a guide.

![](../../.gitbook/assets/be-settings-backup-1.gif)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field/Option</th>
      <th style="text-align:left">Overview</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Schedule automatic backups</td>
      <td style="text-align:left">Enable this to schedule an automatic backup of your configuration to an
        S3 bucket.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cron rule</td>
      <td style="text-align:left">
        <p>Define how often you want the backup to run using the <a href="https://en.wikipedia.org/wiki/Cron">cron</a> format.</p>
        <p><code>[minute] [hour] [day of month] [month] [day of week]</code>
        </p>
        <p>For example, the following would run a backup at 3:41am every Tuesday:</p>
        <p><code>41 3 * * 2</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Access Key ID</td>
      <td style="text-align:left">Enter the access key ID for your S3 bucket.</td>
    </tr>
    <tr>
      <td style="text-align:left">Secret Access Key</td>
      <td style="text-align:left">Enter the secret key for your S3 bucket.</td>
    </tr>
    <tr>
      <td style="text-align:left">Region</td>
      <td style="text-align:left">Enter the region where your bucket is located (for example, <code>us-west-1</code>).</td>
    </tr>
    <tr>
      <td style="text-align:left">Bucket name</td>
      <td style="text-align:left">Enter the name of your S3 bucket.</td>
    </tr>
    <tr>
      <td style="text-align:left">Password protect</td>
      <td style="text-align:left">Enable this to protect your backups with a password.</td>
    </tr>
    <tr>
      <td style="text-align:left">Password</td>
      <td style="text-align:left">Enter the password to set on your backups.</td>
    </tr>
  </tbody>
</table>

![](../../.gitbook/assets/be-settings-backup-s3.png)

Once the settings have been entered, click **Export backup** to perform a manual backup, or **Save backup settings** to save the scheduled backup configuration.

### Restoring from a local file

Restoring a configuration is only possible on a fresh instance of Portainer during the initial installation. When you need to restore Portainer, deploy a fresh instance of Portainer with an empty data volume and choose the **Restore Portainer from backup** option during setup.

![](../../.gitbook/assets/be-settings-backup-2.png)

On the initialization page, expand **Restore Portainer from backup**. Click **Select file** then browse to and select the `tar.gz` backup file. If the backup was originally encrypted, enter the password then click **Restore Portainer**.

The restore might take a few moments. When it has finished, you will be redirected to the login page. You can now log in with your previous credentials and your previous configuration will be restored.

### Restoring from S3

Restoring a configuration is only possible on a fresh instance of Portainer during the initial installation. When you need to restore Portainer, deploy a fresh instance of Portainer with an empty data volume and choose the **Restore Portainer from backup** option during setup, making sure to select **Retrieve from S3**. Complete the fields using the table below as a guide.

| Field/Option | Overview |
| :--- | :--- |
| Access Key ID | Enter the access key ID for your S3 bucket. |
| Secret Access Key | Enter the secret key for your S3 bucket. |
| Region | Enter the region where your bucket is located \(for example, `us-west-1`\). |
| Bucket name | Enter the name of your S3 bucket. |
| Filename | Enter the filename of the backup you want to restore. |
| Password | Enter the password set on your backup \(if any\). |

![](../../.gitbook/assets/be-settings-backup-3.png)

When you're ready, click **Restore Portainer**. The restore might take a few moments. When it has finished, you will be redirected to the login page. You can now log in with your previous credentials and your previous configuration will be restored.
