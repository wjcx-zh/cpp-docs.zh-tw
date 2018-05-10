---
title: 如何： 搜尋資源的符號 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b45780223191c8dacec12d5312f4d2ac724b4d4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-search-for-symbols-in-resources"></a>如何：在資源中搜尋符號
### <a name="to-find-symbols-in-resources"></a>若要尋找資源中的符號  
  
1.  從**編輯**功能表上，選擇**尋找符號**。  
  
2.  在[尋找符號對話方塊](http://msdn.microsoft.com/en-us/63e93d9c-784f-418d-a76a-723da5ff5d96)，請在**尋找**方塊中，從下拉式清單中選取先前的搜尋字串或輸入您想要尋找 （例如，ID_ACCEL1）。  
  
    > [!TIP]
    >  若要使用[規則運算式](/visualstudio/ide/using-regular-expressions-in-visual-studio)進行搜尋，您必須使用[檔案中尋找命令](/visualstudio/ide/reference/find-command)從**編輯**功能表而不是**尋找符號**命令。 若要啟用規則運算式，您必須擁有**使用： 規則運算式**核取方塊中選取[尋找對話方塊](http://msdn.microsoft.com/en-us/dad03582-4931-4893-83ba-84b37f5b1600)。 然後您可以按一下右邊的向右箭號按鈕**尋找**方塊來顯示規則搜尋運算式的清單。 當您從這份清單中選取運算式時，它會替代做為搜尋文字中**尋找**方塊。  
  
3.  選取任何**尋找**選項。  
  
4.  按一下**找下一個**。  
  
    > [!NOTE]
    >  您無法在字串、快速鍵或二進位資源中搜尋符號。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [符號： 資源識別項](../windows/symbols-resource-identifiers.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)