---
title: IDL 屬性、 加入屬性精靈 |Microsoft 文件
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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idl-attributes-add-property-wizard"></a>加入屬性精靈、IDL 屬性
使用 [加入屬性精靈] 的這個頁面來指定任何介面定義語言 (IDL) 設定的屬性。  
  
 **id**  
 設定識別屬性的數值識別碼。 此選項不適用於自訂介面的屬性。 請參閱[識別碼](http://msdn.microsoft.com/library/windows/desktop/aa367040)中*MIDL 參考*。  
  
 **helpcontext**  
 指定的內容識別碼，可讓使用者檢視相關的說明檔中這個屬性的資訊。 請參閱[helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)中*MIDL 參考*。  
  
 **helpstring**  
 指定的字元字串，用來描述它所套用的項目。 根據預設，它設定為 「 屬性*屬性名稱*。 」 請參閱[helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)中*MIDL 參考*。  
  
## <a name="other-options"></a>其他選項  
 並非所有選項都都適用於所有的屬性類型。  
  
|選項|描述|  
|------------|-----------------|  
|**bindable**|表示屬性支援資料繫結。 請參閱[可繫結](http://msdn.microsoft.com/library/windows/desktop/aa366738)中*MIDL 參考*。 內建實作的屬性，此選項預設設定並且無法變更。|  
|**defaultbind**|指出這最佳的單一、 可繫結屬性表示的物件。 請參閱[defaultbind](http://msdn.microsoft.com/library/windows/desktop/aa366790)中*MIDL 參考*。|  
|**displaybind**|表示這個屬性應該顯示為可繫結使用者。 請參閱[displaybind](http://msdn.microsoft.com/library/windows/desktop/aa366804)中*MIDL 參考*。|  
|**immediatebind**|指示資料庫將會立即被告知資料繫結物件的這個屬性的所有變更。 請參閱[immediatebind](http://msdn.microsoft.com/library/windows/desktop/aa367045)中*MIDL 參考*。|  
|**defaultcollelem**|表示內容項目的預設集合存取子函式。 請參閱[defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792)中*MIDL 參考*。|  
|**nonbrowsable**|標籤不會顯示在屬性瀏覽器中的介面或 dispinterface，用以成員。 請參閱[nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117)中*MIDL 參考*。|  
|**requestedit**|表示屬性支援**OnRequestEdit**通知，請參閱[requestedit](http://msdn.microsoft.com/library/windows/desktop/aa367155)中*MIDL 參考*。 內建實作的屬性，此選項預設設定並且無法變更。|  
|**來源**|表示屬性的成員是事件來源。 請參閱[來源](http://msdn.microsoft.com/library/windows/desktop/aa367166)中*MIDL 參考*。|  
|**hidden**|表示屬性存在，但不是會顯示在使用者導向的瀏覽器中。 請參閱[隱藏](http://msdn.microsoft.com/library/windows/desktop/aa366861)中*MIDL 參考*。|  
|**restricted**|指定的屬性無法任意呼叫。 請參閱[限制](http://msdn.microsoft.com/library/windows/desktop/aa367157)中*MIDL 參考*。|  
|`local`|指定的屬性不是遠端 MIDL 編譯器。 請參閱[本機](http://msdn.microsoft.com/library/windows/desktop/aa367071)中*MIDL 參考*。|  
  
## <a name="see-also"></a>另請參閱  
 [加入屬性](../ide/adding-a-property-visual-cpp.md)   
 [名稱、 加入屬性精靈](../ide/names-add-property-wizard.md)   
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)   
 [內建屬性](../ide/stock-properties.md)