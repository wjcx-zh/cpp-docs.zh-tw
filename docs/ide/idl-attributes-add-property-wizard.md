---
title: "加入屬性精靈、IDL 屬性 | Microsoft Docs"
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
  - "vc.codewiz.prop.idlattributes"
dev_langs: 
  - "C++"
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入屬性精靈、IDL 屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用加入屬性精靈這個頁面，來為屬性加入任一個介面定義語言 \(IDL\) 設定。  
  
 **id**  
 設定辨識屬性的數值 ID。  自訂介面的屬性無此選項可用。  請參閱《MIDL 參考》中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 **helpcontext**  
 指定讓使用者在說明檔中檢視屬性資訊的主題代碼。  請參閱《MIDL 參考》中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 **helpstring**  
 指定用來描述所套用之項目的字元字串，  根據預設，它是設定為「屬性 *Property name*」。 請參閱《MIDL 參考》中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
## 其他選項  
 並用所有的屬性型別都可以使用所有選項。  
  
|選項|描述|  
|--------|--------|  
|**bindable**|指示屬性支援資料繫結。  請參閱在《MIDL 參考》中的 [bindable](http://msdn.microsoft.com/library/windows/desktop/aa366738)。  內建屬性實作的這個選項為預設設定，並且無法變更。|  
|**defaultbind**|指示可最佳表示物件的單一、可繫結屬性。  請參閱在《MIDL 參考》中的 [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790)。|  
|**displaybind**|指示屬性應該以可繫結方式顯示給使用者。  請參閱在《MIDL 參考》中的 [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804)。|  
|**immediatebind**|指示資料庫將立即被告知資料繫結物件屬性的所有變更。  請參閱在《MIDL 參考》中的 [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045)。|  
|**defaultcollelem**|指示這個屬性是預設集合某個項目的存取子 \(Accessor\) 函式。  請參閱在《MIDL 參考》中的 [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792)。|  
|**nonbrowsable**|標記不顯示於屬性瀏覽器中的介面或分配介面成員。  請參閱在《MIDL 參考》中的 [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117)。|  
|**requestedit**|指示屬性支援 **OnRequestEdit** 告知，請參閱在《MIDL 參考》中的 [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155)。  內建屬性實作的這個選項為預設設定，並且無法變更。|  
|**source**|指示屬性的成員是一個事件的來源。  請參閱《MIDL 參考》中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|**hidden**|指示屬性存在，但不應該在使用者導向的瀏覽器顯示。  請參閱《MIDL 參考》中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**restricted**|指定屬性不能被隨意呼叫。  請參閱《MIDL 參考》中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|`local`|指定給 MIDL 編譯器，這個屬性不是遠端的。  請參閱《MIDL 參考》中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
  
## 請參閱  
 [加入屬性](../ide/adding-a-property-visual-cpp.md)   
 [名稱、加入屬性精靈](../ide/names-add-property-wizard.md)   
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)   
 [內建屬性](../ide/stock-properties.md)