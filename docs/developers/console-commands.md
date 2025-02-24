# Console Commands
Formie comes with a number of command line utilities that can be run on-demand, or on a set schedule.

## Submissions

### Delete Submissions
You can bulk delete submissions with this command.

Option | Description
--- | ---
`--form-handle` | The form handle(s) to delete submissions from. Can be set to multiple comma-separated handles.
`--form-id` | The form ID(s) to delete submissions from. Can be set to multiple comma-separated IDs.
`--incomplete-only` | Whether to delete only incomplete submissions.
`--spam-only` | Whether to delete only spam submissions.

```shell
./craft formie/submissions/delete --form-handle=form1,anotherForm
```

### Run Integrations
For a provided submission, run the provided integration.

Option | Description
--- | ---
`--submission-id` | The submission ID(s) to use data for. Can be set to multiple comma-separated IDs.
`--integration` | The handle of the integration to trigger.

```shell
./craft formie/submissions/run-integration --submission-id=12345 --integration=mailchimp
```

### Send Email Notification
For a provided submission, send the provided notification.

Option | Description
--- | ---
`--submission-id` | The submission ID(s) to use data for. Can be set to multiple comma-separated IDs.
`--notification-id` | The ID of the notification to trigger.

```shell
./craft formie/submissions/send-notification --submission-id=12345 --notification-id=12
```


## Garbage Collection

### Delete Orphaned Fields
A cleanup tasks to ensure fields aren't orphaned. Not normally required.

```shell
./craft formie/gc/delete-orphaned-fields
```

### Prune Syncs
A cleanup task to ensure Synced Fields are neat. Not normally required.

```shell
./craft formie/gc/prune-syncs
```

### Prune Incomplete Submissions
Deletes any incomplete submissions that exceed the "Maximum Incomplete Submission Age" plugin setting.

```shell
./craft formie/gc/prune-incomplete-submissions
```

### Prune Data Retention Submissions
Deletes any submissions that exceed your data retention form settings.

```shell
./craft formie/gc/prune-data-retention-submissions
```

### Prune Content Tables
A cleanup task to ensure deleted forms have their content tables also deleted. Not normally required.

```shell
./craft formie/gc/prune-content-tables
```

Each of the above commands are also run automatically through [Craft's Garbage Collection](https://craftcms.com/docs/3.x/gc.html), so there's no need to add these commands unless you want fine-grained control over when they run.
