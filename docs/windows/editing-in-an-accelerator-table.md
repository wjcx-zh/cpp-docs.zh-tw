---
title: 編輯快速鍵對應表 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57347b88fe7d54813e06cde6d5f4b3414e79f116
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395802"
---
# <a name="editing-in-an-accelerator-table-c"></a>編輯快速鍵對應表 （c + +）

### <a name="to-edit-in-an-accelerator-table"></a>在快速鍵對應表中編輯

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在資料表中選取一個項目，然後按一下即可啟動就地編輯。

3. 從下拉式方塊中選取，或輸入位置進行變更。

   - 針對[識別碼](id-property.md)，從選取清單或輸入以編輯。

   - 針對[修飾詞](../windows/accelerator-modifier-property.md)，從清單中選取。

   - 針對[金鑰](../windows/accelerator-key-property.md)，從選取清單或輸入以編輯。

   - 針對[型別](../windows/accelerator-type-property.md)，選取**ASCII**或是**VIRTKEY**從清單中。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[編輯快速鍵對應表](../windows/editing-accelerator-tables.md)<br/>
[快速鍵編輯器](../windows/accelerator-editor.md)