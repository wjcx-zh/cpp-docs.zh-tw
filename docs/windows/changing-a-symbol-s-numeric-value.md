---
title: "變更符號 &#39; s 數值 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing.value
dev_langs: C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce2c846d844b79a6ff054bb6c209d1f4653a26d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="changing-a-symbol39s-numeric-value"></a>變更符號 &#39; s 數值
您可以使用單一資源相關聯的符號，[屬性 視窗](/visualstudio/ide/reference/properties-window)變更符號值。 您可以使用[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)若要變更目前未指派給資源的符號值。 如需詳細資訊，請參閱[變更未指定的符號](../windows/changing-unassigned-symbols.md)。  
  
### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>變更指派給單一資源或物件的符號值  
  
1.  在[資源檢視](../windows/resource-view-window.md)，選取的資源。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**屬性**視窗中，輸入符號名稱，後面接著等號和中的整數**識別碼**方塊中，例如：  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 下一次儲存專案時，會在符號標頭檔中儲存新值。 在 [ID] 方塊中，只有符號名稱保持可見狀態；在驗證之後，將不會顯示等號和值。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [符號值限制](../windows/symbol-value-restrictions.md)   
 [預先定義的符號識別碼](../windows/predefined-symbol-ids.md)