---
title: 新增屬性精靈、IDL 屬性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77931296d8d33337c4e630b7327a1ec8fd0a458f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340186"
---
# <a name="idl-attributes-add-property-wizard"></a>加入屬性精靈、IDL 屬性
[新增屬性精靈] 的這個頁面可用來指定屬性的任何介面定義語言 (IDL) 設定。  
  
 **id**  
 設定識別屬性的數值識別碼。 此選項不適用於自訂介面的屬性。 請參閱＜MIDL 參考＞中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 **helpcontext**  
 指定內容識別碼，讓使用者可在說明檔中檢視此屬性的相關資訊。 請參閱＜MIDL 參考＞中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 **helpstring**  
 指定用來描述所套用之項目的字元字串。 根據預設，它會設定為 "property *Property name*"。 請參閱＜MIDL 參考＞中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
## <a name="other-options"></a>其他選項  
 並非所有選項都適用於所有屬性類型。  
  
|選項|描述|  
|------------|-----------------|  
|**bindable**|表示支援資料繫結的屬性。 請參閱＜MIDL 參考＞中的 [bindable](http://msdn.microsoft.com/library/windows/desktop/aa366738)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|  
|**defaultbind**|表示這個單一、可繫結屬性可最佳表示物件。 請參閱＜MIDL 參考＞中的 [defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790)。|  
|**displaybind**|表示這個屬性應向使用者顯示為可繫結。 請參閱＜MIDL 參考＞中的 [displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804)。|  
|**immediatebind**|表示該資料庫將立即被告知此資料繫結物件屬性的所有變更。 請參閱＜MIDL 參考＞中的 [immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045)。|  
|**defaultcollelem**|表示屬性是預設集合項目的存取子函式。 請參閱＜MIDL 參考＞中的 [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792)。|  
|**nonbrowsable**|標記不應顯示在屬性瀏覽器中的介面或分配介面成員。 請參閱＜MIDL 參考＞中的 [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117)。|  
|**requestedit**|表示屬性支援 **OnRequestEdit** 通知。請參閱＜MIDL 參考＞中的 [requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|  
|**source**|表示屬性的成員是事件來源。 請參閱＜MIDL 參考＞中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|**hidden**|表示屬性存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**restricted**|指定無法任意呼叫屬性。 請參閱＜MIDL 參考＞中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|`local`|向 MIDL 編譯器指定屬性不是遠端。 請參閱＜MIDL 參考＞中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
  
## <a name="see-also"></a>請參閱  
 [新增屬性](../ide/adding-a-property-visual-cpp.md)   
 [新增屬性精靈、名稱](../ide/names-add-property-wizard.md)   
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)   
 [內建屬性](../ide/stock-properties.md)