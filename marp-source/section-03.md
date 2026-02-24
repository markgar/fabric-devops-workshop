---
marp: true
theme: workshop
paginate: true
transition: fade
---

# Deployment Rules

What happens when Dev and Prod need different settings?

---

# The Problem

Your notebook uses a **default lakehouse**. When you deploy to Prod, which lakehouse does it use?

<div class="flow" style="margin: 20px 0;">
  <div class="card card-md card-dev">
    <div class="card-title-md">Dev Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item bg-orange">Transform Orders</div>
      <div class="arrow-label">↓ default</div>
      <div class="box box-item bg-blue">Sales Bronze</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label-sm">Deploy</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-md card-prod">
    <div class="card-title-md">Prod Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item bg-orange">Transform Orders</div>
      <div class="arrow-label">↓ default</div>
      <div class="box box-item" style="background: #DC3545; color: #fff;">Sales Bronze (DEV!) 💥</div>
    </div>
  </div>
</div>

> 💡 **Auto-binding** handles the simple case — when all items deploy together to the same workspace, Fabric fixes the references automatically. But it can't help with shared lakehouses, external data sources, or cross-workspace references.

---

# How Deployment Rules Work

A deployment rule says: *"When deploying to this stage, swap this setting."*

<div class="flow" style="margin: 20px 0;">
  <div class="card card-md card-dev">
    <div class="card-title-md">Dev Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item bg-orange">Transform Orders</div>
      <div class="arrow-label">↓ default</div>
      <div class="box box-item bg-blue">Sales Bronze (Dev)</div>
    </div>
  </div>
  <div class="flow-col-center">
    <div class="arrow-label-sm">Deploy +</div>
    <div style="font-size: 0.55em; color: #2E8B57; font-weight: bold;">Rule Applied ✓</div>
    <span class="arrow-md">→</span>
  </div>
  <div class="card card-md card-prod">
    <div class="card-title-md">Prod Workspace</div>
    <div class="flow-col" style="margin-top: 6px; gap: 3px;">
      <div class="box box-item" style="background: #C96E2E;">Transform Orders</div>
      <div class="arrow-label">↓ default</div>
      <div class="box box-item bg-green">Sales Bronze (Prod) ✅</div>
    </div>
  </div>
</div>

- Rules are configured on the **target stage** (where you're deploying *to*)
- Set them once — they apply on **every deployment**
- Works for lakehouses, data connections, parameters, and more

---

# What You'll Do in Section 3

<div class="centered-block">
<div class="left-aligned">

<div class="step">
  <div class="step-number">1</div>
  <div class="step-text">Create a <strong>lakehouse</strong> and connect it to your notebook</div>
</div>

<div class="step">
  <div class="step-number">2</div>
  <div class="step-text">Deploy the notebook and lakehouse to <strong>Production</strong></div>
</div>

<div class="step">
  <div class="step-number">3</div>
  <div class="step-text">Configure a <strong>deployment rule</strong> to swap the lakehouse</div>
</div>

<div class="step">
  <div class="step-number">4</div>
  <div class="step-text">Deploy again and <strong>verify</strong> the rule works</div>
</div>

</div>
</div>

Let's get started!
