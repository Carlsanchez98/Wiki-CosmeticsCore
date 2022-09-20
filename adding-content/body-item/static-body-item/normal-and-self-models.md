# Normal and self models

## Introduction

It's important to have two separated models because the self model will avoid getting the player view occupied by the cosmetic and potentially cause annoyances during the gameplay (placing blocks, attacking, walking).

{% tabs %}
{% tab title="Without the self model" %}
![](../../../.gitbook/assets/2022-08-17\_17.47.53.png)

![](../../../.gitbook/assets/2022-08-17\_17.48.40.png)
{% endtab %}

{% tab title="With the self model" %}
![](../../../.gitbook/assets/2022-08-17\_17.48.16.png)

![](../../../.gitbook/assets/2022-08-17\_17.48.40.png)
{% endtab %}
{% endtabs %}

### Normal model

A normal model is the model which is shown to every player but the local player (yourself).

### Self model

A self model is the model which is shown ONLY to the local player (yourself).

## Implementing the fix

### Step 1

You have to make a copy of your `.json` model file, rename it `_self.json`.\
For example: `squirrel_tail.json` -> `squirrel_tail_self.json`

### Step 2

Decide a new **CustomModelData** for that item and add it to the item file or use ItemAdder to automate the process (depends on your needs, refer to [ItemsAdder wiki ](https://itemsadder.devs.beer/)to learn how to create items).

In this example I use `400008` for the **normal** model and `400009` for the **self** model.

`assets/minecraft/models/item/XXX.json`

```json
{
  "predicate": { "custom_model_data": 400008 },
  "model": "cosmetics:body/squirrel_tail"
},
{
  "predicate": { "custom_model_data": 400009 },
  "model": "cosmetics:body/squirrel_tail_self"
},
```

### Step 3

Edit your cosmetics configuration and add the **self** model.

```yaml
  squirrel_tail:
    display_name: "Squirrel Tail"
    type: BODY_ITEM
    model:
      gui: potion:400008
      normal: potion:400008
      self: potion:400009   ### <------ HERE
    dye:
      enabled: false
```

### Step 4

This is the most important step, you have to edit the **self** model.\
You have to move the model down like that, then view it ingame until you're satisfied with the result.

This requires you to check ingame a few times until the model is correctly positioned, it requires some tries to achieve the perfect location, but you can easily use some of the example models  in order to avoid losing time.vi

{% embed url="https://youtu.be/dmQI35Xd4Js" %}

## Differences

### Normal model

![](<../../../.gitbook/assets/image (1).png>)

### Self model

![](<../../../.gitbook/assets/image (3).png>)