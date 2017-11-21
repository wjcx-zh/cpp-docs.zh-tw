---
title: "進行 ATL 物件變成無法建立 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.objects
dev_langs: C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38aa9f5fae45c9d5fa1e413763bd5fa2e65ab795
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="making-an-atl-object-noncreatable"></a>進行 ATL 物件變成無法建立
您可以變更 atl COM 物件的屬性，讓用戶端無法直接建立物件。 在此情況下，物件會將透過方法呼叫所傳回的另一個物件而直接建立。  
  
### <a name="to-make-an-object-noncreatable"></a>使物件變成無法建立  
  
1.  移除[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)物件。 如果您想要該物件會變成無法建立，但要註冊的控制項，取代與 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)。  
  
2.  新增[noncreatable](../../windows/noncreatable.md) .idl 檔案中 coclass 此屬性。 例如:   
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>另請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

