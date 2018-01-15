---
title: "避免堆積競爭 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f17f73efc8fba19bb129e3b118f8a4357444aad0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="avoidance-of-heap-contention"></a>避免堆積競爭
由 MFC 和 ATL 提供的預設字串管理員是全域堆積之上的簡單包裝函式。 這個全域的 heap 是完全安全的執行緒，也就是說，多個執行緒可以配置和釋放記憶體從它同時而不損毀的堆積。 為了提供安全執行緒，堆積已序列化的存取權本身。 這通常是以關鍵區段或類似的鎖定機制來完成。 每當兩個執行緒嘗試同時存取堆積，一個執行緒會封鎖直到另一個執行緒的要求。 對於許多應用程式，很少會發生這種情況下，且在堆積的鎖定機制的效能影響可不予理會。 不過，對於應用程式經常從多個執行緒存取堆積堆積的鎖定爭用會造成更慢速度如果它是單一執行緒 （即使有多個 Cpu 的電腦） 上執行應用程式。  
  
 使用應用程式[CStringT](../atl-mfc-shared/reference/cstringt-class.md)特別容易堆積競爭因為作業`CStringT`物件經常需要在字串緩衝區重新配置。  
  
 減少競爭執行緒之間的堆積情況的其中一種方式是讓每個執行緒私用的執行緒本機堆積中配置的字串。 只要字串配置與特定的執行緒配置器僅用於該執行緒，配置器不需要具備執行緒安全。  
  
## <a name="example"></a>範例  
 下列範例會示範將字串，該執行緒上使用它自己私用非安全執行緒的堆積配置的執行緒程序：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]  
  
## <a name="comments"></a>註解  
 無法使用這個相同的執行緒程序執行多個執行緒，但因為每個執行緒有其專屬堆積是沒有執行緒之間的競爭。 此外，每個堆積都不是安全執行緒的事實提供明顯增加效能，即使只有一個執行緒的複本正在執行。 這是不使用昂貴連鎖的作業，以防止並行存取堆積的結果。  
  
 更複雜的執行緒程序中，可能會很方便的指標儲存至執行緒的字串管理員執行緒區域儲存區 (TLS) 插槽中。 這可讓其他執行緒的程序來存取執行緒的字串管理員所呼叫的函式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

