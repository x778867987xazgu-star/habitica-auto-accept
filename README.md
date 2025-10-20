# habitica-auto-accept
name: Habitica Quest Auto-Accept

# This workflow runs automatically every hour
on:
  schedule:
    - cron: "0 * * * *"  # Runs every hour on the hour
  workflow_dispatch:      # Allows you to manually trigger it

jobs:
  accept_quest:
    runs-on: ubuntu-latest
    steps:
      - name: Send request to Habitica API
        run: |
          curl -X POST "https://habitica.com/api/v3/groups/party/quests/accept" \
          -H "x-api-user: ${{ secrets.HABITICA_USER_ID }}" \
          -H "x-api-key: ${{ secrets.HABITICA_API_TOKEN }}" \
          -H "Content-Type: application/json"
