---
title: "讓 ATL 物件變成無法建立 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: b812c2d4bfeb0663d62051c05829f25dc7139faf
ms.lasthandoff: 02/24/2017

---
# <a name="making-an-atl-object-noncreatable"></a>讓 ATL 物件變成無法建立
您可以變更 ATL COM 物件的屬性，以便用戶端無法直接建立物件。 在此情況下，物件就會透過方法呼叫所傳回的另一個物件，而不是直接建立。  
  
### <a name="to-make-an-object-noncreatable"></a>若要讓物件變成無法建立  
  
1.  移除[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)物件。 如果您想要變成無法建立，而註冊控制項的物件，取代使用 OBJECT_ENTRY_AUTO [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](http://msdn.microsoft.com/library/abdc093c-6502-42de-8419-b7ebf45299d1)。  
  
2.  新增[noncreatable](../../windows/noncreatable.md) coclass.idl 檔中此屬性。 例如:   
  
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
 [使用 ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)


