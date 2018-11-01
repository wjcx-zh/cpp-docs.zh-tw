---
title: 快速鍵類型屬性 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
ms.openlocfilehash: 00699f31b821aa508feec9ffe062d768f27ee5a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475579"
---
# <a name="accelerator-type-property-c"></a>快速鍵類型屬性 （c + +）

加速器**型別**屬性決定快速鍵 ID 相關聯的快速鍵組合是虛擬的按鍵組合或 ASCII/ANSI 機碼值：

- 如果**型別**屬性是 ASCII，[修飾詞](../windows/accelerator-modifier-property.md)只能`None`或`Alt`，或它可能會使用加速器**Ctrl** （所指定的索引鍵上述的金鑰`^`)。

- 如果**型別**屬性是 VIRTKEY 的任意組合`Modifier`和`Key`值無效。

   > [!NOTE]
   > 如果您想要快速鍵對應表中輸入值，且值為 ASCII/ANSI，只要按一下**型別**從下拉式清單中的選取 ASCII 與資料表中的項目。 不過，如果您使用**下一步 輸入的按鍵**命令 (**編輯**功能表) 來指定`Key`，您必須變更**型別**屬性從 VIRTKEY 為 ASCII *之前先*輸入`Key`程式碼。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[設定快速鍵屬性](../windows/setting-accelerator-properties.md)<br/>
[快速鍵編輯器](../windows/accelerator-editor.md)