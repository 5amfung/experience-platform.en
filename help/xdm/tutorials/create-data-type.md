---
keywords: Experience Platform;home;popular topics;ui;XDM;XDM system;experience data model;Experience data model;Experience Data Model;data model;Data Model;schema registry;Schema Registry;schema;Schema;schemas;Schemas;create;data type;data types;
solution: Experience Platform
title: Create and edit data types using the Schema Registry UI
topic: tutorial
type: Tutorial
description: This tutorial uses the Experience Platform UI to walk you through the steps to compose a custom data type.
---

# Create and edit data types using the Experience Platform UI

In Experience Data Model (XDM), data types are used as reference-type fields in classes or mixins in the same way as basic literal fields, with the key difference being that data types can define multiple sub-fields. While similar to mixins in that they allow for the consistent use of a multi-field structure, data types are more flexible because they can be included anywhere in the schema structure whereas mixins can only be added at the root level. 

Adobe Experience Platform provides many standard data types that can be used to cover a wide variety of common experience management use cases. However, you can also define your own custom data types in order to serve your unique business needs.

This tutorial covers the steps for creating and editing custom data types in the Platform user interface.

## Prerequisites

This tutorial requires a working understanding of XDM System. Refer to the [XDM overview](../home.md) for an introduction to the role of XDM within the Experience Platform ecosystem, and the [basics of schema composition](../schema/composition.md) for how data types contribute to XDM schemas.

While not required for this tutorial, it is recommended that you also follow the tutorial on [composing a schema in the UI](./create-schema-ui.md) to familiarize yourself with the various capabilities of the [!DNL Schema Editor].

## Open the [!DNL Schema Editor] for a data type

In the Platform UI, select **[!UICONTROL Schemas]** in the left navigation to open the [!UICONTROL Schemas] workspace, then select the **[!UICONTROL Data types]** tab. A list of available data types is displayed, including those defined by Adobe as well as those created by your organization.

![](../images/tutorials/create-datatype/data-types-tab.png)

From here, you have two options:

* [Create a new data type](#create)
* [Select an existing data type to edit](#edit)

### Create a new data type {#create}

From the **[!UICONTROL Data types]** tab, select **[!UICONTROL Create data type]**.

![](../images/tutorials/create-datatype/create.png)

The [!DNL Schema Editor] appears, showing the current structure of the new data type in the canvas. On the right-hand side of the editor, you can provide a display name and optional description for the data type. Ensure that you provide a unique and concise name for your data type, as that is how it will be identified when adding it to a schema.

This tutorial creates a data type that describes a restaurant property, so the data type is given a display name of "Restaurant".

![](../images/tutorials/create-datatype/data-type-properties.png)

Skip ahead to the [next section](#add-fields) to start adding fields to the data type.

### Edit an existing data type

Only custom data types defined by your organization can be edited. To narrow down the displayed list, select the filter icon (![Filter Icon](../images/tutorials/create-datatype/filter.png)) to reveal controls for filtering based on [!UICONTROL Owner]. Select **[!UICONTROL Customer]** to show only custom data types owned by your organization.

Select the data type you want to edit from the list to open the right rail, showing the details of the data type. Select the name of the data type in the right rail to open its structure in the [!DNL Schema Editor].

![](../images/tutorials/create-datatype/edit.png)

## Add fields to the data type {#add-fields}

To start adding fields to the data type, select the **plus (+)** icon next to the root-level field in the canvas. A new field appears below, and the right rail updates to display controls for the new field.

![](../images/tutorials/create-datatype/new-field.png)

Use the right-rail controls to provide a **[!UICONTROL Field name]**, **[!UICONTROL Display name]**, and **[!UICONTROL Type]** for the field. Note that a field's type may be a basic scalar type (such as a string, integer, or boolean), or can represent another multi-field data type defined by Adobe or your organization.

The Restaurant data type requires a string field to represent the restaurant's name. As such, the [!UICONTROL Field name] is set as "name" and the [!UICONTROL Type] is set as [!UICONTROL String]. Select **[!UICONTROL Apply]** to apply the changes to the field.

![](../images/tutorials/create-datatype/name-field.png)

Continue following the same process for adding additional fields, starting by selecting the **plus (+)** icon next to the root-level field and providing the configuration details in the right rail.

The Restaurant data type now has additional fields for brand, seating capacity, and floor space.

![](../images/tutorials/create-datatype/more-fields.png)

In addition to basic fields, you can also nest additional data types within your custom data type. For example, the Restaurant data type requires a field that represents the property's physical address. In this scenario, you can add a new "address" field which is assigned the standard data type "[!UICONTROL Postal address]".

![](../images/tutorials/create-datatype/address-field.png)

This demonstrates how flexible data types can be in terms of describing your data: data types can employ fields which are also data types, which themselves can contain further data types, and so on. This allows you to abstract and reuse common data patterns throughout your XDM schemas, making it easier to represent complex data structures.

Once you have finished adding fields to the data type, select **[!UICONTROL Save]** to save your changes and add the data type to the [!DNL Schema Library].

## Add the data type to a mixin

Once you have created a data type, you can start using it in your schemas. Since XDM schemas are composed of a class and zero or more mixins, fields provided by a data type cannot be added to a schema directly. Instead, they must be included in a class or a mixin.

>[!NOTE]
>
>This section focuses on adding a data type to a mixin, since this is the most common pattern for custom data types. However, you can also apply the same steps to add your data type to a class instead.

You can add the data type to an existing mixin, or create a new mixin entirely. In either case, you must open the [!DNL Schema Editor] for a schema that you plan to add the new data type to, either by selecting an existing schema from the **[!UICONTROL Browse]** tab, or by creating a new schema entirely.

Once you have the schema open in the [!DNL Schema Editor], select the mixin you want to add the data type to in the left rail. If the schema does not have an appropriate mixin, follow the steps to [create a new mixin](./create-schema-ui.md#define-mixin) to add to the schema instead, and make sure that the mixin is selected in the left rail.

![](../images/tutorials/create-datatype/mixin-selected.png)

Select the **plus (+)** icon next to the schema's name to add a new field to the selected mixin. When selecting the **[!UICONTROL Type]** property for the field, the name of the data type you created earlier is now available in the dropdown list. You can start typing the name of the data type to help locate it easier.

![](../images/tutorials/create-datatype/add-data-type.png)

Select your data type from the list, then select **[!UICONTROL Apply]**. The schema field updates in the canvas to show the structured sub-fields provided by the data type. If you save the schema by selecting **[!UICONTROL Save]**, the mixin is saved as well, allowing you to reuse the mixin in additional schemas belonging to the same class.

![](../images/tutorials/create-datatype/data-type-added.png)

>[!NOTE]
>
>Mixins are only compatible with one class. If you wish to use your data type in additional schemas based on different classes, you must follow the above steps to add the data type to additional mixins intended to extend those classes.

## Next steps

This tutorial covered how to create and edit data types, and how to add them to mixins using the [!DNL Schema Editor]. To learn more about working with data types in the UI, including how to convert a multi-field object into a data type, see the [schema creation tutorial](./create-schema-ui.md#datatype).

To learn how to create a data type using the Schema Registry API, see the [data types endpoint guide](../api/data-types.md#create).