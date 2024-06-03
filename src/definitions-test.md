# Instance Models

This section transforms the problem defined in the [problem description](./problem-description.md) into one which is expressed in mathematical terms. It uses concrete symbols defined in the [data definitions](./data-definitions.md) to replace the abstract symbols in the models identified in [theoretical models](./theoretical-models.md) and [general definitions](./general-definitions.md).

## Calculation of Landing Time <div style="float: right; color: grey; font-size: 12pt;"><em>IM:calOfLandingTime</em></div>

**Input**: \\({v_{\text{launch}}}\\), \\(θ\\)

**Output**: \\({t_{\text{flight}}}\\)

**Input Constraints**: \\[{v_{\text{launch}}}\gt{}0\\] \\[0\lt{}θ\lt{}\frac{π}{2}\\]


**Output Constraints**: \\[{t_{\text{flight}}}\gt{}0\\]

**Equation**: \\[{t_{\text{flight}}}=\frac{2 {v_{\text{launch}}} \sin\left(θ\right)}{g}\\]

<details>

<summary><b>Description</b></summary>

- \\({t_{\text{flight}}}\\) is the flight duration (\\({\text{s}}\\)) 
- \\({v_{\text{launch}}}\\) is the launch speed (\\(\frac{\text{m}}{\text{s}}\\)) 
- \\(θ\\) is the launch angle (\\({\text{rad}}\\)) 
- \\(g\\) is the magnitude of gravitational acceleration (\\(\frac{\text{m}}{\text{s}^{2}}\\))

</details>

<br>

<details>

<summary><b>Notes</b></summary>

- The constraint \\(0\lt{}θ\lt{}\frac{π}{2}\\) is from [A:posXDirection](./assumptions.md#posXDirection) and [A:yAxisGravity](./assumptions.md#yAxisGravity), and is shown in [Fig:Launch](./physical-sys-description.md#Figure:Launch). 
- \\(g\\) is defined in [A:gravAccelValue](./assumptions.md#gravAccelValue). 
- The constraint \\({t_{\text{flight}}}\gt{}0\\) is from [A:timeStartZero](./assumptions.md#timeStartZero).

</details>

<br>

<details>

<summary><b>RefBy</b></summary>

[IM:calOfLandingDist](./instance-models.md#IM:calOfLandingDist), [FR:Output-Values](./functional-req.md#outputValues), and [FR:Calculate-Values](./functional-req.md#calcValues)

</details>

<br>

<details>

<summary><b>Detailed derivation of flight duration</b></summary>

We know that \\({{p_{\text{y}}}^{\text{i}}}=0\\) ([A:launchOrigin](./assumptions.md#launchOrigin)) and \\({{a_{\text{y}}}^{\text{c}}}=-g\\) ([A:accelYGravity](./assumptions.md#accelYGravity)). Substituting these values into the y-direction of [GD:posVec](./general-definitions.md#GD:posVec) gives us:

\\[{p_{\text{y}}}={{v_{\text{y}}}^{\text{i}}} t-\frac{g t^{2}}{2}\\]

To find the time that the projectile lands, we want to find the \\(t\\) value (\\({t_{\text{flight}}}\\)) where \\({p_{\text{y}}}=0\\) (since the target is on the \\(x\\)-axis from [A:targetXAxis](./assumptions.md#targetXAxis)). From the equation above we get:

\\[{{v_{\text{y}}}^{\text{i}}} {t_{\text{flight}}}-\frac{g {t_{\text{flight}}}^{2}}{2}=0\\]

Dividing by \\({t_{\text{flight}}}\\) (with the constraint \\({t_{\text{flight}}}\gt{}0\\)) gives us:

\\[{{v_{\text{y}}}^{\text{i}}}-\frac{g {t_{\text{flight}}}}{2}=0\\]

Solving for \\({t_{\text{flight}}}\\) gives us:

\\[{t_{\text{flight}}}=\frac{2 {{v_{\text{y}}}^{\text{i}}}}{g}\\]

From [DD:speedIY](./data-definitions.md#DD:speedIY) (with \\({v^{\text{i}}}={v_{\text{launch}}}\\)) we can replace \\({{v_{\text{y}}}^{\text{i}}}\\):

\\[{t_{\text{flight}}}=\frac{2 {v_{\text{launch}}} \sin\left(θ\right)}{g}\\]

</details>

## IM:calOfLandingDist 

**Label**: Calculation of landing position

**Input**: \\({v_{\text{launch}}}\\), \\(θ\\)

**Output**: \\({p_{\text{land}}}\\)

**Input Constraints**: \\[{v_{\text{launch}}}\gt{}0\\] \\[0\lt{}θ\lt{}\frac{π}{2}\\]

**Output Constraints**: \\[{p_{\text{land}}}\gt{}0\\]

**Equation**: \\[{p_{\text{land}}}=\frac{2 {v_{\text{launch}}}^{2} \sin\left(θ\right) \cos\left(θ\right)}{g}\\]

<details>

<summary><b>Description</b></summary>

- \\({p_{\text{land}}}\\) is the landing position (\\({\text{m}}\\)) 
- \\({v_{\text{launch}}}\\) is the launch speed (\\(\frac{\text{m}}{\text{s}}\\)) 
- \\(θ\\) is the launch angle (\\({\text{rad}}\\)) 
- \\(g\\) is the magnitude of gravitational acceleration (\\(\frac{\text{m}}{\text{s}^{2}}\\))

</details>

<br>

<details>

<summary><b>Notes</b></summary>

- The constraint \\(0\lt{}θ\lt{}\frac{π}{2}\\) is from [A:posXDirection](./assumptions.md#posXDirection) and [A:yAxisGravity](./assumptions.md#yAxisGravity), and is shown in [Fig:Launch](./physical-sys-description.md#Figure:Launch). 
- \\(g\\) is defined in [A:gravAccelValue](./assumptions.md#gravAccelValue).
- The constraint \\({p_{\text{land}}}\gt{}0\\) is from [A:posXDirection](./assumptions.md#posXDirection).

</details>

<br>

<details>

<summary><b>RefBy</b></summary>

[IM:offsetIM](./instance-models.md#IM:offsetIM) and [FR:Calculate-Values](./functional-req.md#calcValues)

</details>

<br>

<details>

<summary><b>Detailed derivation of landing position</b></summary>

We know that \\({{p_{\text{x}}}^{\text{i}}}=0\\) ([A:launchOrigin](./assumptions.md#launchOrigin)) and \\({{a_{\text{x}}}^{\text{c}}}=0\\) ([A:accelXZero](./assumptions.md#accelXZero)). Substituting these values into the x-direction of [GD:posVec](./general-definitions.md#GD:posVec) gives us:

\\[{p_{\text{x}}}={{v_{\text{x}}}^{\text{i}}} t\\]

To find the landing position, we want to find the \\({p_{\text{x}}}\\) value (\\({p_{\text{land}}}\\)) at flight duration (from [IM:calOfLandingTime](./instance-models.md#IM:calOfLandingTime)):

\\[{p_{\text{land}}}=\frac{{{v_{\text{x}}}^{\text{i}}}\cdot{}2 {v_{\text{launch}}} \sin\left(θ\right)}{g}\\]

From [DD:speedIX](./data-definitions.md#DD:speedIX) (with \\({v^{\text{i}}}={v_{\text{launch}}}\\)) we can replace \\({{v_{\text{x}}}^{\text{i}}}\\):

\\[{p_{\text{land}}}=\frac{{v_{\text{launch}}} \cos\left(θ\right)\cdot{}2 {v_{\text{launch}}} \sin\left(θ\right)}{g}\\]

Rearranging this gives us the required equation:

\\[{p_{\text{land}}}=\frac{2 {v_{\text{launch}}}^{2} \sin\left(θ\right) \cos\left(θ\right)}{g}\\]

</details>