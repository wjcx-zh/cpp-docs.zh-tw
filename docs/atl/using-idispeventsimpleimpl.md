---
title: 使用 IDispEventSimpleImpl (ATL) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed21c862d61686e86efd684a6e88795e4b7bbe51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-idispeventsimpleimpl"></a>使用 IDispEventSimpleImpl
當使用`IDispEventSimpleImpl`來處理事件，您必須：  
  
-   衍生您的類別從[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)。  
  
-   將事件接收對應加入至類別。  
  
-   定義[_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md)結構描述的事件。  
  
-   將項目加入至事件接收器對應使用[SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info)巨集。  
  
-   實作您想要處理的方法。  
  
-   通知與取消通知的事件來源。  
  
## <a name="example"></a>範例  
 下列範例會示範如何處理**DocumentChange**引發事件，這是由 Word 的**應用程式**物件。 此事件在定義為方法**ApplicationEvents**分配介面。  
  
 這個範例取自[ATLEventHandling 範例](../visual-cpp-samples.md)。  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 此範例會使用`#import`從 Word 的型別程式庫產生必要的標頭檔。 如果您想要使用此範例與 Word 其他版本，您必須指定正確的 mso dll 檔案。 例如，Office 2000 提供 mso9.dll 並 OfficeXP 提供 mso.dll。 此程式碼已經過簡化 stdafx.h:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]  
  
 從實際用於此範例中的類型程式庫的唯一資訊是 Word 的 CLSID**應用程式**物件和 IID **ApplicationEvents**介面。 在編譯時期只用這項資訊。  
  
 下列程式碼會出現在 Simple.h。 註解所加註相關的程式碼：  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]  
  
 下列程式碼取自 Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [事件處理](../atl/event-handling-and-atl.md)   
 [ATLEventHandling 範例](../visual-cpp-samples.md)

