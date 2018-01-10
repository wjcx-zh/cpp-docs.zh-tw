---
title: "支援 IDispEventImpl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDispEventImpl
dev_langs: C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bf10a68ae15743a637df2dee52bee83c3dfcbe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-idispeventimpl"></a>支援 IDispEventImpl
此範本類別[IDispEventImpl](../atl/reference/idispeventimpl-class.md)可用來對 ATL 類別中的連接點接收提供支援。 連接點接收可讓您的類別來處理從外部 COM 物件引發的事件。 這些連接點接收對應的事件接收對應，您的類別所提供。  
  
 若要正確地實作連接點接收為您的類別，您必須完成下列步驟：  
  
-   匯入的每個外部物件的類型程式庫  
  
-   宣告`IDispEventImpl`介面  
  
-   宣告事件接收對應  
  
-   通知與取消通知的連接點  
  
 實作連接點接收所需的步驟是藉由修改僅標頭檔 (.h) 的類別來完成。  
  
## <a name="importing-the-type-libraries"></a>匯入類型程式庫  
 每個外部物件您想要處理的事件，您必須匯入類型程式庫。 此步驟定義可以處理的事件，並提供使用當您宣告事件接收對應的資訊。 [#Import](../preprocessor/hash-import-directive-cpp.md)指示詞可用來完成這項作業。 加入必要`#import`行指示詞，您將支援標頭檔 (.h) 類別的每個分派介面。  
  
 下列範例會匯入外部 COM 伺服器的類型程式庫 (`MSCAL.Calendar.7`):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  您必須擁有個別`#import`陳述式將會支援每個外部型別程式庫。  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>宣告 IDispEventImpl 介面  
 既然您已匯入的每個分派介面的類型程式庫，您需要宣告個別`IDispEventImpl`每個外部分派介面的介面。 修改類別的宣告，藉由新增`IDispEventImpl`介面宣告的每個外部物件。 如需有關參數的詳細資訊，請參閱[IDispEventImpl](../atl/reference/idispeventimpl-class.md)。  
  
 下列程式碼宣告兩個連接點接收，`DCalendarEvents`介面，由類別實作的 COM 物件`CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>宣告事件接收對應  
 為了讓由適當的函式來處理的事件通知，您的類別必須將每個事件路由至正確的處理常式。 藉由宣告事件接收對應可達到此目的。  
  
 ATL 提供數個巨集， [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map)， [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)，和[SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)，可讓此對應更容易。 標準格式如下所示：  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 下列範例會宣告事件接收對應具有兩個事件處理常式：  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 實作已幾乎完成。 最後一個步驟是有關通知及外部介面的取消通知。  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>通知和取消通知 IDispEventImpl 介面  
 最後一個步驟是實作的方法，將會通知 （或取消通知） 的所有連線點在適當時機。 外部用戶端與物件之間的通訊發生之前，必須完成此通知。 您的物件顯示之前，您物件支援的每個外部分派介面會查詢的輸出介面。 建立連接，並輸出介面的參考用來處理事件的物件。 此程序稱為 「 通知 」。  
  
 物件結束外部介面之後，應該類別不再使用這些通知的外寄的介面。 此程序稱為 「 取消通知 」。  
  
 COM 物件的唯一特性，因為此程序各有不同，在詳細資料和執行，不同的實作。 已超出本主題的範圍和不解決這些詳細資料。  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)

