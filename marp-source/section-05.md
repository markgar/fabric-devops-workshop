---
marp: true
theme: workshop
paginate: true
transition: fade
---


# Variable Libraries

Environment-specific configuration without changing code

---

# The Problem with Hard-Coding

Your notebook works in Dev. You deploy to Prod. But the settings are wrong.

<div class="comparison" style="gap: 30px;">

<div>
<h4>Dev</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm bg-mono" style="text-align: left; font-size: 0.6em;">table = "workshop_seed_dev"</div>
  <div class="box box-sm bg-mono" style="text-align: left; font-size: 0.6em;">row_count = 10</div>
  <div class="box box-sm bg-mono" style="text-align: left; font-size: 0.6em;">label = "dev"</div>
</div>
</div>

<div style="display: flex; align-items: center;">
  <div class="flow-col-center">
    <div class="arrow-label-sm">Deploy</div>
    <span class="arrow-md">→</span>
  </div>
</div>

<div>
<h4>Prod 💥</h4>
<div class="flow-col" style="gap: 6px;">
  <div class="box box-sm" style="background: #fde8e8; color: #DC3545; text-align: left; font-size: 0.6em; border: 1px solid #DC3545;">table = "workshop_seed_dev"</div>
  <div class="box box-sm" style="background: #fde8e8; color: #DC3545; text-align: left; font-size: 0.6em; border: 1px solid #DC3545;">row_count = 10</div>
  <div class="box box-sm" style="background: #fde8e8; color: #DC3545; text-align: left; font-size: 0.6em; border: 1px solid #DC3545;">label = "dev"</div>
</div>
</div>

</div>

<br/>

You could edit code per environment — but that defeats the purpose of automation. You need **configuration that changes per stage, not code that changes per stage**.

---

# How Variable Libraries Work

One library, multiple **value sets** — each stage picks the right one

<div class="flow" style="margin: 16px 0; gap: 16px;">
  <div class="card card-sm" style="border: 2px solid #8B5CF6; background: #f3eefe; padding: 10px 14px;">
    <div class="card-title-sm">📦 EnvConfig</div>
    <div style="font-size: 0.5em; margin-top: 6px;">
      <table style="font-size: 1em; border-collapse: collapse; width: 100%;">
        <tr style="border-bottom: 1px solid #ccc;"><th style="text-align:left; padding: 2px 6px;">Variable</th><th style="padding: 2px 6px;">Dev</th><th style="padding: 2px 6px;">Prod</th></tr>
        <tr><td style="padding: 2px 6px; font-family: monospace;">RunLabel</td><td style="padding: 2px 6px;">dev</td><td style="padding: 2px 6px;">prod</td></tr>
        <tr><td style="padding: 2px 6px; font-family: monospace;">RowCount</td><td style="padding: 2px 6px;">10</td><td style="padding: 2px 6px;">100</td></tr>
        <tr><td style="padding: 2px 6px; font-family: monospace;">TableName</td><td style="padding: 2px 6px;">seed_dev</td><td style="padding: 2px 6px;">seed_prod</td></tr>
      </table>
    </div>
  </div>
</div>

<div class="flow" style="margin: 12px 0; gap: 20px;">
  <div class="card card-sm card-dev" style="padding: 10px 14px;">
    <div class="card-title-sm">Dev Workspace</div>
    <div style="font-size: 0.5em; color: #555; margin-top: 4px;">Active: <strong>Dev</strong> value set</div>
  </div>
  <div class="card card-sm card-prod" style="padding: 10px 14px;">
    <div class="card-title-sm">Prod Workspace</div>
    <div style="font-size: 0.5em; color: #555; margin-top: 4px;">Active: <strong>Prod</strong> value set</div>
  </div>
</div>

- Same code reads variables → gets different values per stage
- Works with **notebooks**, **pipelines**, **dataflows**, **shortcuts**, and more

---

# What You'll Do in Section 5

<div class="centered-block">
<div class="left-aligned">

<div class="step">
  <div class="step-number">1</div>
  <div class="step-text">Create a <strong>variable library</strong> with Dev and Prod value sets</div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="step-text">Update your notebook to <strong>read variables</strong> instead of hard-coded values</div>
</div>

<div class="step">
  <div class="step-number">3</div>
  <div class="step-text"><strong>Deploy</strong> and set the active value set per stage</div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="step-text">Run in Prod and verify <strong>different behavior, same code</strong></div>
</div>

</div>
</div>

Let's get started!
