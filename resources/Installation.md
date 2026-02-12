# Installation et Mise à jour

## Installation 

git subtree split --prefix=expert-agent -b expert-agent
git remote add -f skills-lib https://github.com/labs-web/agent-skills.git
git subtree add --prefix .agent/skills/expert-agent skills-lib expert-agent --squash

## Mise à jour 
git subtree pull --prefix .agent/skills/expert-agent skills-lib expert-agent --squash
git subtree push --prefix .agent/skills/expert-agent skills-lib expert-agent