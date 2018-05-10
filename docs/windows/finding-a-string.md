---
title: 尋找字串 |Microsoft 文件
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
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3763baf0f085dc72040ab22c9efd38e8aa8068f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="finding-a-string"></a>尋找字串
您可以搜尋的一或多個字串在字串資料表中，並使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)與**檔案中尋找**命令 (**編輯**功能表) 以找出所有的執行個體的字串符合的模式。  
  
### <a name="to-find-a-string-in-the-string-table"></a>以字串資料表中尋找字串  
  
1.  開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**編輯**功能表上，按一下 **尋找和取代**，然後選擇 **尋找**。  
  
3.  在**尋找**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找之字串的標題文字或資源識別碼。  
  
4.  選取任何**尋找**選項。  
  
5.  按一下**找下一個**。  
  
    > [!TIP]
    >  若要搜尋檔案時，請使用規則運算式，使用**檔案中尋找**命令。 輸入的規則運算式比對模式，或按一下右邊的按鈕**尋找**方塊來顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替代做為搜尋文字中**尋找**方塊。 如果您使用規則運算式，請務必**使用： 規則運算式**選取核取方塊。  
  
 如需將資源加入至 managed 專案 （其會以 common language runtime 為目標） 的資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [字串編輯器](../windows/string-editor.md)   

