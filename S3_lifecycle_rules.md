# S3 Lifecycle Rules Demo

## Objective

To demonstrate Amazon S3 Lifecycle Rules for automatically transitioning objects between storage classes and deleting objects after a specified period.

## Steps

### 1. Create an S3 Bucket

1. Log in to the AWS Management Console.
2. Go to **S3**.
3. Click **Create bucket**.
4. Enter a unique bucket name.
5. Select the required AWS Region.
6. Create the bucket.

### 2. Upload a Test File

Create a test file:

```bash
echo "S3 Lifecycle Demo" > test.txt
```

Upload `test.txt` to the S3 bucket.

### 3. Create a Lifecycle Rule

Go to:

**S3 → Bucket → Management → Lifecycle rules → Create lifecycle rule**

Enter:

```text
Lifecycle rule name: demo-lifecycle-rule
```

Choose:

```text
Apply to all objects in the bucket
```

### 4. Configure Storage Transitions

Configure the following transitions:

```text
After 30 days  → Standard-IA
After 60 days  → Glacier Flexible Retrieval
```

The objects will automatically move to cheaper storage classes as they become older.

### 5. Configure Object Expiration

Enable:

```text
Expire current versions of objects
After 90 days
```

Objects matching the lifecycle rule will be automatically deleted after the configured period.

## Lifecycle Flow

```text
S3 Standard
     |
     | After 30 days
     v
S3 Standard-IA
     |
     | After 60 days
     v
Glacier Flexible Retrieval
     |
     | After 90 days
     v
Object Deleted
```

## Lifecycle Rule Configuration

| Action                                   |    Days |
| ---------------------------------------- | ------: |
| Transition to Standard-IA                | 30 days |
| Transition to Glacier Flexible Retrieval | 60 days |
| Delete Object                            | 90 days |

## Verification

1. Go to **S3 → Bucket → Management**.
2. Open **Lifecycle rules**.
3. Verify that `demo-lifecycle-rule` is enabled.
4. Check the rule configuration and transitions.

## Result

The S3 Lifecycle Rule was successfully created to automatically transition objects to different storage classes and delete them after the specified retention period.

## Technologies Used

* Amazon S3
* S3 Lifecycle Rules
* S3 Standard
* S3 Standard-IA
* S3 Glacier Flexible Retrieval
