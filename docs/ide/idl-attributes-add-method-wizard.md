---
title: "IDL 屬性、加入方法精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.method.idlattrib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "加入方法精靈 [C++]"
  - "IDL 屬性, 加入方法精靈"
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDL 屬性、加入方法精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個 \[加入方法精靈\] 頁面，指定方法的介面定義語言 \(IDL\) 設定。  
  
 **id**  
 設定辨識方法的數值 ID。  請參閱《MIDL 參考》中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 自訂介面和 MFC 分配介面無法使用這個方塊。  
  
 **call\_as**  
 指定這個區域方法可被對應的遠端方法的名稱。  請參閱《MIDL 參考》中的 [call\_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)。  
  
 MFC 分配介面無法使用。  
  
 **helpcontext**  
 指定使用者在說明檔中檢視這個方法相關資訊的主題代碼。  請參閱《MIDL 參考》中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 MFC 分配介面無法使用。  
  
 **helpstring**  
 指定用來描述所套用之項目的字元字串，  預設為「方法名稱方法」。 請參閱《MIDL 參考》中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
 MFC 分配介面無法使用。  
  
 **其他屬性**  
 MFC 分配介面無法使用。  
  
|屬性|描述|  
|--------|--------|  
|**hidden**|表示方法存在，但不應該在使用者導向的瀏覽器顯示。  請參閱《MIDL 參考》中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**source**|表示方法的成員是一個事件的來源。  請參閱《MIDL 參考》中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|`local`|指定 MIDL 編譯器，這個方法不是遠端的方法。  請參閱《MIDL 參考》中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
|**restricted**|指定方法不能被隨意呼叫。  請參閱《MIDL 參考》中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|**vararg**|指定方法接收不定個數的引數。  若要完成這項工作，最後一個引數必須是包含所有剩餘引數的 **VARIANT** 型別安全陣列。  請參閱《MIDL 參考》中的 [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)。|  
  
## 請參閱  
 [加入方法](../ide/adding-a-method-visual-cpp.md)   
 [加入方法精靈](../ide/add-method-wizard.md)