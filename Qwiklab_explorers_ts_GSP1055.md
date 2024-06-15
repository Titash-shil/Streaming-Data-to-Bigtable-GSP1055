# Streaming Data to Bigtable || [GSP1055](https://www.cloudskillsboost.google/focuses/92498?&parent=catalog) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell

### Task 1 > Create a Bigtable instance and table:- ```Need to complete using console```

```
echo project = `gcloud config get-value project` \
    >> ~/.cbtrc

echo instance = sandiego \
    >> ~/.cbtrc

cbt createtable current_conditions \
    families="lane"

cat > prepare_disk.sh <<'EOF_END'
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
source /training/project_env.sh
/training/sensor_magic.sh
EOF_END

ZONE="$(gcloud compute instances list --project=$DEVSHELL_PROJECT_ID --format='value(ZONE)' | head -n 1)"

gcloud compute scp prepare_disk.sh training-vm:/tmp --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet

gcloud compute ssh training-vm --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet --command="bash /tmp/prepare_disk.sh"
```

## Open another new cloud shell and run the below commands:

```
cat > prepare_disk_1.sh <<'EOF_END'
source /training/project_env.sh
cd ~/training-data-analyst/courses/streaming/process/sandiego
./run_oncloud.sh $DEVSHELL_PROJECT_ID $BUCKET CurrentConditions --bigtable
EOF_END

ZONE="$(gcloud compute instances list --project=$DEVSHELL_PROJECT_ID --format='value(ZONE)' | head -n 1)"


gcloud compute scp prepare_disk_1.sh training-vm:/tmp --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet

gcloud compute ssh training-vm --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet --command="bash /tmp/prepare_disk_1.sh"

```

## Once you get score on Task 1-3 then only run this command, otherwise you won't get full score on that lab totally...

```
echo "Listing all Dataflow jobs:"
gcloud dataflow jobs list


export JOB_ID=$(gcloud dataflow jobs list | grep JOB_ID: | awk '{print $2}')

gcloud dataflow jobs cancel $JOB_ID

cbt deletetable current_conditions

echo -e "\e[1m\e[34mhttps://console.cloud.google.com/dataflow/jobs?referrer=search&project=$DEVSHELL_PROJECT_ID\e[0m"
```

# Congratulations ..!! You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
