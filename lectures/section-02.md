---
marp: true
theme: default
paginate: true
transition: fade
---

<!-- _class: lead -->

# Deployment Pipelines

Moving Fabric content from Dev → Test → Prod

---

# Why Separate Environments?

<div style="display: flex; gap: 40px; justify-content: center; margin: 20px 0;">

<div>
<h4 style="margin: 0 0 10px 0;">❌ Without Environments</h4>
<div style="display: flex; flex-direction: column; gap: 6px;">
  <div style="border-radius: 6px; padding: 8px 16px; background: #DC3545; color: #fff; font-size: 0.7em;">Developers break production</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #DC3545; color: #fff; font-size: 0.7em;">Users see half-finished work</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #DC3545; color: #fff; font-size: 0.7em;">No way to test before go-live</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #DC3545; color: #fff; font-size: 0.7em;">No audit trail of changes</div>
</div>
</div>

<div>
<h4 style="margin: 0 0 10px 0;">✅ With Environments</h4>
<div style="display: flex; flex-direction: column; gap: 6px;">
  <div style="border-radius: 6px; padding: 8px 16px; background: #28A745; color: #fff; font-size: 0.7em;">Dev is isolated from production</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #28A745; color: #fff; font-size: 0.7em;">Test before promoting</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #28A745; color: #fff; font-size: 0.7em;">Controlled, deliberate releases</div>
  <div style="border-radius: 6px; padding: 8px 16px; background: #28A745; color: #fff; font-size: 0.7em;">Clear history of what deployed</div>
</div>
</div>

</div>

---

# Fabric Deployment Pipelines

A Fabric feature that lets you **deploy content between workspaces** in stages

<div style="display: flex; gap: 8px; justify-content: center; align-items: center; margin: 30px 0;">
  <div style="border: 2px solid #82B366; border-radius: 10px; padding: 16px 24px; background: #e8f5e9; text-align: center;">
    <div style="font-weight: bold; font-size: 0.8em;">🛠️ Development</div>
    <div style="font-size: 0.55em; color: #555; margin-top: 4px;">Build & iterate</div>
  </div>
  <span style="font-size: 1.5em;">→</span>
  <div style="border: 2px solid #D4A843; border-radius: 10px; padding: 16px 24px; background: #fef9e7; text-align: center;">
    <div style="font-weight: bold; font-size: 0.8em;">🧪 Test</div>
    <div style="font-size: 0.55em; color: #555; margin-top: 4px;">Validate & review</div>
  </div>
  <span style="font-size: 1.5em;">→</span>
  <div style="border: 2px solid #2E8B57; border-radius: 10px; padding: 16px 24px; background: #e8f5f0; text-align: center;">
    <div style="font-weight: bold; font-size: 0.8em;">🏭 Production</div>
    <div style="font-size: 0.55em; color: #555; margin-top: 4px;">Live for users</div>
  </div>
</div>

- Each stage is backed by a **separate Fabric workspace**
- Deploy **all items** or **selected items** between stages
- Pipelines can have **2 to 10 stages**

---

# How It Works

<div style="display: flex; gap: 10px; justify-content: center; align-items: center; margin: 20px 0;">
  <div style="border: 2px solid #82B366; border-radius: 10px; padding: 12px 16px; background: #e8f5e9; text-align: center;">
    <div style="font-weight: bold; font-size: 0.7em;">Dev Workspace</div>
    <div style="display: flex; flex-direction: column; gap: 3px; margin-top: 6px;">
      <div style="border-radius: 4px; padding: 3px 8px; background: #4A90D9; color: #fff; font-size: 0.5em;">Lakehouse</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #E8833A; color: #fff; font-size: 0.5em;">Notebook</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #8B5CF6; color: #fff; font-size: 0.5em;">Semantic Model</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #F5C542; color: #000; font-size: 0.5em;">Report</div>
    </div>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center;">
    <div style="font-size: 0.55em; color: #555;">Deploy</div>
    <span style="font-size: 1.4em;">→</span>
  </div>
  <div style="border: 2px solid #D4A843; border-radius: 10px; padding: 12px 16px; background: #fef9e7; text-align: center;">
    <div style="font-weight: bold; font-size: 0.7em;">Test Workspace</div>
    <div style="display: flex; flex-direction: column; gap: 3px; margin-top: 6px;">
      <div style="border-radius: 4px; padding: 3px 8px; background: #4A90D9; color: #fff; font-size: 0.5em;">Lakehouse</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #E8833A; color: #fff; font-size: 0.5em;">Notebook</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #8B5CF6; color: #fff; font-size: 0.5em;">Semantic Model</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #F5C542; color: #000; font-size: 0.5em;">Report</div>
    </div>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center;">
    <div style="font-size: 0.55em; color: #555;">Deploy</div>
    <span style="font-size: 1.4em;">→</span>
  </div>
  <div style="border: 2px solid #2E8B57; border-radius: 10px; padding: 12px 16px; background: #e8f5f0; text-align: center;">
    <div style="font-weight: bold; font-size: 0.7em;">Prod Workspace</div>
    <div style="display: flex; flex-direction: column; gap: 3px; margin-top: 6px;">
      <div style="border-radius: 4px; padding: 3px 8px; background: #4A90D9; color: #fff; font-size: 0.5em;">Lakehouse</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #E8833A; color: #fff; font-size: 0.5em;">Notebook</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #8B5CF6; color: #fff; font-size: 0.5em;">Semantic Model</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #F5C542; color: #000; font-size: 0.5em;">Report</div>
    </div>
  </div>
</div>

- Deployment **copies item definitions** from one workspace to another
- Items are **created or updated** in the target workspace
- Each workspace can have **different data connections** and **security settings**

---

# Tagging Releases

Use **Git tags** to mark a point-in-time snapshot of your codebase

<div style="display: flex; gap: 6px; justify-content: center; align-items: center; margin: 30px 0;">
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #6C8EBF;"></div>
  <div style="width: 40px; height: 2px; background: #999;"></div>
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #6C8EBF;"></div>
  <div style="width: 40px; height: 2px; background: #999;"></div>
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #82B366; border: 3px solid #2E8B57;"></div>
  <div style="width: 40px; height: 2px; background: #999;"></div>
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #6C8EBF;"></div>
  <div style="width: 40px; height: 2px; background: #999;"></div>
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #6C8EBF;"></div>
  <div style="width: 40px; height: 2px; background: #999;"></div>
  <div style="border-radius: 50%; width: 16px; height: 16px; background: #82B366; border: 3px solid #2E8B57;"></div>
</div>

<div style="display: flex; gap: 6px; justify-content: center; align-items: flex-start; margin: 0;">
  <div style="width: 56px;"></div>
  <div style="width: 56px;"></div>
  <div style="text-align: center; font-size: 0.6em; font-weight: bold; color: #2E8B57; width: 56px;">🏷️ v1.0</div>
  <div style="width: 56px;"></div>
  <div style="width: 56px;"></div>
  <div style="width: 56px;"></div>
  <div style="text-align: center; font-size: 0.6em; font-weight: bold; color: #2E8B57; width: 56px;">🏷️ v2.0</div>
</div>

- Tags let you **label a release** (e.g., `v1.0`, `v2.0`)
- You can always **go back and view** what was in a release
- Tag before you deploy — it creates a **record of what went to production**

---

# The Release Workflow

<div style="display: flex; flex-direction: column; gap: 12px; align-items: center; margin: 20px 0;">

<div style="display: flex; gap: 12px; align-items: center;">
  <div style="border-radius: 50%; width: 36px; height: 36px; background: #4063D8; color: #fff; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 0.9em;">1</div>
  <div style="font-size: 0.8em;">Build and test your changes in the <strong>Dev</strong> workspace</div>
</div>

<div style="display: flex; gap: 12px; align-items: center;">
  <div style="border-radius: 50%; width: 36px; height: 36px; background: #4063D8; color: #fff; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 0.9em;">2</div>
  <div style="font-size: 0.8em;"><strong>Commit</strong> your changes to the Git repository</div>
</div>

<div style="display: flex; gap: 12px; align-items: center;">
  <div style="border-radius: 50%; width: 36px; height: 36px; background: #4063D8; color: #fff; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 0.9em;">3</div>
  <div style="font-size: 0.8em;"><strong>Tag</strong> the release in Git (e.g., <code>v1.0</code>)</div>
</div>

<div style="display: flex; gap: 12px; align-items: center;">
  <div style="border-radius: 50%; width: 36px; height: 36px; background: #4063D8; color: #fff; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 0.9em;">4</div>
  <div style="font-size: 0.8em;"><strong>Deploy</strong> from Dev → Test → Prod using the deployment pipeline</div>
</div>

</div>

This gives you a **repeatable, auditable** release process
