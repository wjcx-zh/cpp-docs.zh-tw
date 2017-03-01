---
title: "ATL 專案中加入新的介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.interface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 8e4916c60310dd8dcbf0bb9e8c1f151309a32621
ms.lasthandoff: 02/24/2017

---
# <a name="adding-a-new-interface-in-an-atl-project"></a>ATL 專案中加入新的介面
當您將介面加入物件或控制項時，您會建立介面的虛設常式的函式的每個方法。 在您的物件或控制項，您可以加入目前現有的類型程式庫中找到的介面。 此外，您可以在其中加入介面的類別必須實作[BEGIN_COM_MAP](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)巨集或，如果專案使用屬性，您必須先`coclass`屬性。  
  
 您可以將新的介面加入控制項有兩種︰ 手動或使用類別檢視 中的程式碼精靈。  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>若要使用類別檢視中的程式碼精靈，將介面新增至現有的物件或控制項  
  
1.  在[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下控制項的類別名稱。 例如，完整的控制權或複合控制項或實作 BEGIN_COM_MAP 巨集在其標頭檔中的任何其他控制項類別。  
  
2.  在捷徑功能表，按一下 **新增**，然後按一下 **實作介面**。  
  
3.  選取要在中實作的介面[實作介面精靈](../../ide/implement-interface-wizard.md)。 如果介面不存在於任何可用的型別程式庫，然後您必須將它手動加入的.idl 檔案。  
  
### <a name="to-add-a-new-interface-manually"></a>若要手動新增新的介面  
  
1.  .Idl 檔案中加入新介面的定義。  
  
2.  衍生物件或介面的控制項。  
  
3.  建立新[COM_INTERFACE_ENTRY](http://msdn.microsoft.com/library/c5363b8b-a1a2-471e-ad3a-d472f6c356c5)介面或者，如果專案使用屬性，加入`coclass`屬性。  
  
4.  實作的介面上的方法。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)


