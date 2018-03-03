---
title: "IDL 屬性、 加入方法精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9792f8b7758ff5a1e5742b6643d9f73931bce6f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 屬性, 加入方法精靈
使用加入方法精靈的這個頁面來指定方法的任何介面定義語言 (IDL) 設定。  
  
 **id**  
 設定識別的方法的數字 ID。 請參閱[識別碼](http://msdn.microsoft.com/library/windows/desktop/aa367040)中*MIDL 參考*。  
  
 此方塊無法使用自訂介面，並不能用於 MFC 分配介面。  
  
 **call_as**  
 指定遠端方法，這個區域方法可以對應的名稱。 請參閱[call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)中*MIDL 參考*。  
  
 不能用於 MFC 分配介面。  
  
 **helpcontext**  
 指定的內容識別碼，可讓使用者檢視相關的說明檔中，這個方法的資訊。 請參閱[helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)中*MIDL 參考*。  
  
 不能用於 MFC 分配介面。  
  
 **helpstring**  
 指定的字元字串，用來描述它所套用的項目。 根據預設，它設定為"方法*方法名稱*。 」 請參閱[helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)中*MIDL 參考*。  
  
 不能用於 MFC 分配介面。  
  
 **其他屬性**  
 不能用於 MFC 分配介面。  
  
|屬性|描述|  
|---------------|-----------------|  
|**hidden**|表示方法存在，但不是會顯示在使用者導向的瀏覽器中。 請參閱[隱藏](http://msdn.microsoft.com/library/windows/desktop/aa366861)中*MIDL 參考*。|  
|**來源**|表示方法的成員是事件來源。 請參閱[來源](http://msdn.microsoft.com/library/windows/desktop/aa367166)中*MIDL 參考*。|  
|`local`|指定這個方法不是遠端 MIDL 編譯器。 請參閱[本機](http://msdn.microsoft.com/library/windows/desktop/aa367071)中*MIDL 參考*。|  
|**restricted**|指定此方法無法被任意呼叫。 請參閱[限制](http://msdn.microsoft.com/library/windows/desktop/aa367157)中*MIDL 參考*。|  
|**vararg**|指定此方法採用可變引數數目。 若要達成此目的，最後一個引數必須是安全陣列的**VARIANT**包含其餘的引數的型別。 請參閱[vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)中*MIDL 參考*。|  
  
## <a name="see-also"></a>請參閱  
 [加入方法](../ide/adding-a-method-visual-cpp.md)   
 [新增方法精靈](../ide/add-method-wizard.md)