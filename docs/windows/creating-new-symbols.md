---
title: "建立新的符號 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b01146297307de92d3e79844ac0488b5ff13e29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-new-symbols"></a>建立新的符號
當您開始新的專案時，您可能會發現先對應符號名稱，再建立將指派到的資源很方便。  
  
### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>使用資源符號對話方塊建立新符號  
  
1.  在[資源符號對話方塊](../windows/resource-symbols-dialog-box.md)，選擇**新增**。  
  
2.  在**名稱**方塊中，輸入符號名稱。  
  
3.  接受指派的符號值。  
  
     -或-  
  
     在**值**方塊中，輸入新值。  
  
4.  按一下**確定**符號清單中加入新的符號。  
  
 如果您輸入的符號名稱已經存在，此時會出現訊息方塊，說明已定義使用該名稱的符號。 您不能定義兩個或多個具有相同名稱的符號，但您可以定義具有相同數值的不同符號。 如需詳細資訊，請參閱[符號名稱限制](../windows/symbol-name-restrictions.md)和[符號值限制](../windows/symbol-value-restrictions.md)。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [檢視資源符號](../windows/viewing-resource-symbols.md)   
 [預先定義的符號識別碼](../windows/predefined-symbol-ids.md)