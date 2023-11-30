# ASN11
import requests

def create_github_issue(repo_owner, repo_name, title, body, labels=[]):
    url = f'https://api.github.com/repos/{repo_owner}/{repo_name}/issues'
    headers = {'Authorization': 'token YOUR_ACCESS_TOKEN'}

    issue_data = {
        'title': title,
        'body': body,
        'labels': labels
    }

    response = requests.post(url, json=issue_data, headers=headers)

    if response.status_code == 201:
        print(f'Issue created successfully: {response.json()["html_url"]}')
    else:
        print(f'Failed to create issue. Status code: {response.status_code}, Message: {response.text}')

# Заменете следните данни с вашите:
repo_owner = 'alexviki59'
repo_name = 'ASN11'
issue_title = 'New Task'
issue_body = 'Курсов проект'
issue_labels = ['bug', 'enhancement']

create_github_issue(repo_owner, repo_name, issue_title, issue_body, issue_labels)

