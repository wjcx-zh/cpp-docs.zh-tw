---
title: 新增或刪除字串 |Microsoft Docs
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
- string tables, deleting strings
- strings [C++], deleting in string tables
- string tables, adding strings
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a470aa5bb1b24ab2fe549f098a83c29e5d0828
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464145"
---
# <a name="adding-or-deleting-a-string"></a>加入或刪除字串
您可以快速地插入至字串資料表使用字串編輯器的新項目。 新的字串會放在資料表結尾處，並指定下一個可用的識別項。 接著，您就可以編輯中的識別碼、 值或標題的屬性[屬性 視窗](/visualstudio/ide/reference/properties-window)視。  
  
 字串編輯器可確保您不使用已在使用的識別碼。 如果您已經在使用選取的識別碼，字串編輯器就會通知您，然後指派 泛用的唯一識別碼，例如 IDS_STRING58113。  
  
### <a name="to-add-a-string-table-entry"></a>若要加入的字串資料表項目  
  
1.  開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  字串資料表中按一下滑鼠右鍵，然後選擇 **新的字串**從捷徑功能表。  
  
3.  在 [**字串**編輯器中，選取**識別碼**從 ID] 下拉式清單或類型識別碼直接就地。  
  
4.  編輯**值**，如有必要。  
  
5.  輸入的項目**標題**。  
  
    > [!NOTE]
    >  在 Windows 字串資料表中不允許 null 的字串。 如果您是 null 字串的字串資料表中建立項目，您會收到訊息，要求您 請輸入字串為此資料表項目。  
  
### <a name="to-delete-a-string-table-entry"></a>若要刪除的字串資料表項目  
  
1.  選取您要刪除的項目。  
  
2.  在 **編輯**功能表上，按一下**刪除**。  
  
 \-或-  
  
-   以滑鼠右鍵按一下您想要刪除，然後選擇 的字串**刪除**從捷徑功能表。  
  
 \-或-  
  
-   按下**刪除**索引鍵。  
  
 如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)在 *.NET Framework 開發人員指南。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5)並[逐步解說： 使用資源以利用 ASP.NET 進行當地語系化](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [字串編輯器](../windows/string-editor.md)   