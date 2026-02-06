---
marp: true
theme: default
paginate: true
transition: fade
---

<!-- _class: lead -->

# What is CI/CD?

<div style="display: flex; gap: 60px; justify-content: center; align-items: flex-start; margin: 10px 0;">

<div>
<h4 style="margin: 0 0 8px 0;">🔀 Continuous Integration</h4>
<div style="display: flex; gap: 12px; align-items: center;">
  <div style="display: flex; flex-direction: column; gap: 4px;">
    <div style="border-radius: 6px; padding: 6px 14px; background: #6C8EBF; color: #fff; text-align: center; font-size: 0.7em;">Developer A</div>
    <div style="border-radius: 6px; padding: 6px 14px; background: #6C8EBF; color: #fff; text-align: center; font-size: 0.7em;">Developer B</div>
    <div style="border-radius: 6px; padding: 6px 14px; background: #6C8EBF; color: #fff; text-align: center; font-size: 0.7em;">Developer C</div>
  </div>
  <div style="display: flex; flex-direction: column; gap: 4px;">
    <div style="font-size: 1.2em; text-align: center;">→</div>
    <div style="font-size: 1.2em; text-align: center;">→</div>
    <div style="font-size: 1.2em; text-align: center;">→</div>
  </div>
  <div style="border-radius: 50%; padding: 16px 12px; background: #4063D8; color: #fff; text-align: center; font-size: 0.65em; font-weight: bold;">Main<br/>Codebase</div>
</div>
</div>

<div>
<h4 style="margin: 0 0 8px 0;">🚀 Continuous Delivery</h4>
<div style="display: flex; gap: 8px; align-items: center;">
  <div style="border-radius: 6px; padding: 8px 18px; background: #82B366; color: #fff; font-size: 0.75em; font-weight: bold;">Dev</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 6px; padding: 8px 18px; background: #D4A843; color: #fff; font-size: 0.75em; font-weight: bold;">Test</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 6px; padding: 8px 18px; background: #2E8B57; color: #fff; font-size: 0.75em; font-weight: bold;">Prod</div>
</div>
</div>

</div>

**CI** — Multiple developers push code to the main codebase
**CD** — Code moves from Dev → Test → Prod

---

# Fabric CI/CD Capabilities

- **Git Integration**
- **Deployment Pipelines**
- **Variable Library**
- **Workspace Item Types**
- **Item Definitions**
- **Fabric REST APIs**

---

# Fabric Items

Workspace items are the building blocks used to build a Fabric solution

<h4>Example of a simple Fabric solution</h4>

<div style="display: flex; gap: 10px; justify-content: center; align-items: center; margin: 10px 0;">
  <div style="border-radius: 8px; padding: 10px 16px; background: #4A90D9; color: #fff; text-align: center; font-size: 0.75em; font-weight: bold;">Lakehouse</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 8px; padding: 10px 16px; background: #E8833A; color: #fff; text-align: center; font-size: 0.75em; font-weight: bold;">Notebook</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 8px; padding: 10px 16px; background: #4A90D9; color: #fff; text-align: center; font-size: 0.75em; font-weight: bold;">Lakehouse</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 8px; padding: 10px 16px; background: #8B5CF6; color: #fff; text-align: center; font-size: 0.75em; font-weight: bold;">Semantic<br/>Model</div>
  <span style="font-size: 1.2em;">→</span>
  <div style="border-radius: 8px; padding: 10px 16px; background: #F5C542; color: #000; text-align: center; font-size: 0.75em; font-weight: bold;">Report</div>
</div>

<br/>

- Some Fabric solutions can be deployed to a **single workspace**
- More complex Fabric solutions can be spread across **multiple workspaces**

---

# Fabric Git Integration

- Fabric supported Git providers: **Azure DevOps**, **GitHub**, and **GitHub Enterprise**
- Other Git providers will be added over time
- Git connections are managed like other connections in Fabric
- Fabric Git integration is enabled at **workspace scope**
- A workspace is connected to a **branch** in a Git repository

<div style="display: flex; gap: 12px; justify-content: center; align-items: center; margin: 30px 0;">
  <div style="border: 2px solid #0078D4; border-radius: 10px; padding: 16px 24px; background: #e8eef7; text-align: center;">
    <div style="font-weight: bold; font-size: 0.8em;">🏢 Workspace</div>
    <div style="font-size: 0.6em; color: #555; margin-top: 4px;">Notebooks, Lakehouses, Reports...</div>
  </div>
  <span style="font-size: 1.5em;">⇄</span>
  <div style="border: 2px solid #F05033; border-radius: 10px; padding: 16px 24px; background: #fdf0ed; text-align: center;">
    <div style="font-weight: bold; font-size: 0.8em;">🔀 Git Repository</div>
    <div style="font-size: 0.6em; color: #555; margin-top: 4px;">Branch: main</div>
  </div>
</div>

---

# Fabric Item Serialization in Git

When you connect a workspace to a Git branch...

<div style="display: flex; gap: 12px; justify-content: center; align-items: center; margin: 16px 0;">
  <div style="border: 2px solid #0078D4; border-radius: 10px; padding: 14px 18px; background: #e8eef7; text-align: center;">
    <div style="font-weight: bold; font-size: 0.75em;">🏢 Workspace</div>
    <div style="display: flex; flex-direction: column; gap: 3px; margin-top: 6px;">
      <div style="border-radius: 4px; padding: 3px 8px; background: #4A90D9; color: #fff; font-size: 0.55em;">BronzeLakehouse</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #E8833A; color: #fff; font-size: 0.55em;">Transform Bronze to Silver</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #8B5CF6; color: #fff; font-size: 0.55em;">Sales Model</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #F5C542; color: #000; font-size: 0.55em;">Sales Report</div>
    </div>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 2px;">
    <div style="font-size: 0.6em; color: #555;">Commit</div>
    <span style="font-size: 1.4em;">→</span>
    <span style="font-size: 1.4em;">←</span>
    <div style="font-size: 0.6em; color: #555;">Update</div>
  </div>
  <div style="border: 2px solid #F05033; border-radius: 10px; padding: 14px 18px; background: #fdf0ed; text-align: center;">
    <div style="font-weight: bold; font-size: 0.75em;">🔀 Git Branch</div>
    <div style="display: flex; flex-direction: column; gap: 3px; margin-top: 6px;">
      <div style="border-radius: 4px; padding: 3px 8px; background: #eee; color: #333; font-size: 0.55em; font-family: monospace;">BronzeLakehouse.Lakehouse/</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #eee; color: #333; font-size: 0.55em; font-family: monospace;">Transform Bronze to Silver.Notebook/</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #eee; color: #333; font-size: 0.55em; font-family: monospace;">Sales Model.SemanticModel/</div>
      <div style="border-radius: 4px; padding: 3px 8px; background: #eee; color: #333; font-size: 0.55em; font-family: monospace;">Sales Report.Report/</div>
    </div>
  </div>
</div>

- **Commit →** Fabric serializes workspace item definitions and writes definition files to the branch
- **Update ←** Fabric can create/update workspace items from item definitions in the Git branch
