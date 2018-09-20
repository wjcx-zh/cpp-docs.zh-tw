---
title: 移動或複製快速鍵對應表項目到另一個資源指令碼檔案 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
ms.assetid: 7b4dc149-c972-4ab2-8477-76c52b6feb5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d3f75ef8c2820c227716e3208ff2cded54d1fd7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414728"
---
# <a name="moving-or-copying-an-accelerator-table-entry-to-another-resource-script-file-c"></a>移動或複製快速鍵對應表項目到另一個資源指令碼檔案 （c + +）

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>將快速鍵對應表項目移動或複製到另一個資源指令碼檔案

1. 在這兩個資源指令碼檔案中開啟快速鍵對應表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您要移動的項目。

3. 從**編輯**功能表上，選擇**複製**或是**剪下**。

4. 選取目標資源指令碼檔案中的項目。

5. 從**編輯**功能表上，選擇**貼上**。

   > [!NOTE]
   > 您也可以使用快速鍵進行複製及貼上。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[編輯快速鍵對應表](../windows/editing-accelerator-tables.md)<br/>
[快速鍵編輯器](../windows/accelerator-editor.md)