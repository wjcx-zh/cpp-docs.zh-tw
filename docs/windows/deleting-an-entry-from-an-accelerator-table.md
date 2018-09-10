---
title: 刪除快速鍵對應表 （c + +） 中的項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
ms.assetid: cc9cd499-dc04-4fe6-9393-a3e471e115a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 747e0db32a73a277ef26e18e787e3e5a31f69578
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315115"
---
# <a name="deleting-an-entry-from-an-accelerator-table-c"></a>刪除快速鍵對應表 （c + +） 中的項目

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>刪除快速鍵對應表中的項目

1. 開啟快速鍵對應表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 選取您要刪除的項目。 (按住**Ctrl**或是**Shift**鍵同時按一下來選取多個項目。)

3. 以滑鼠右鍵按一下，然後選擇 **刪除**從捷徑功能表 (或選取**刪除**從**編輯**功能表)。

\-或-

- 按下**刪除**索引鍵。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[編輯快速鍵對應表](../windows/editing-accelerator-tables.md)  
[快速鍵編輯器](../windows/accelerator-editor.md)