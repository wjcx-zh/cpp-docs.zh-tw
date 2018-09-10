---
title: 新增或刪除字串資源 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c22990c504700ab82ae0d7542420a3f82db4d73
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314036"
---
# <a name="adding-or-deleting-a-string-resource-c"></a>新增或刪除字串資源 （c + +）

您可以很快地插入至字串資料表使用的新項目**字串**編輯器。 新的字串會放在資料表結尾處，並指定下一個可用的識別項。 然後您可以編輯**識別碼**，**值**，或**標題**中的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)視。

**字串**編輯器可確保您不使用已在使用的識別碼。 如果您選取的識別碼已經在使用中，**字串**編輯器將會通知您，並將指定的泛用的唯一識別碼，例如`IDS_STRING58113`。

### <a name="to-add-a-string-table-entry"></a>若要加入的字串資料表項目

1. 開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 字串資料表中按一下滑鼠右鍵，然後選擇 **新的字串**從捷徑功能表。

3. 在 [**字串**編輯器中，選取**識別碼**從 ID] 下拉式清單或類型識別碼直接就地。

4. 編輯**值**，如有必要。

5. 輸入的項目**標題**。

   > [!NOTE]
   > 在 Windows 字串資料表中不允許 null 的字串。 如果您是 null 字串的字串資料表中建立項目，您會收到訊息，要求您 請輸入字串為此資料表項目。

### <a name="to-delete-a-string-table-entry"></a>若要刪除的字串資料表項目

1. 選取您要刪除的項目。

2. 在 **編輯**功能表上，按一下**刪除**。

\-或-

- 以滑鼠右鍵按一下您想要刪除，然後選擇 的字串**刪除**從捷徑功能表。

\-或-

- 按下**刪除**索引鍵。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\))。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)  