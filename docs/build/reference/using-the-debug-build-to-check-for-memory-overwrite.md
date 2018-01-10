---
title: "使用偵錯版檢查記憶體覆寫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f18a13992e41cd88bc8edec44f16b02da38ad10c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>使用偵錯版檢查記憶體覆寫
若要使用偵錯版檢查記憶體覆寫，您必須先重建專案，以偵錯。 然後，移至您的應用程式的最前頭`InitInstance`函式，並加入下行：  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 偵錯記憶體配置器會將所有記憶體配置周圍的保護位元組。 不過，這些保護位元組並沒有任何效用，除非您檢查是否已經變更 （這會指示記憶體覆寫）。 否則，這只是提供的緩衝區，事實上，可能會讓您消除記憶體覆寫。  
  
 藉由開啟`checkAlwaysMemDF`，您將會強制對進行呼叫的 MFC`AfxCheckMemory`函式每次呼叫**新**或**刪除**進行。 如果偵測到記憶體覆寫，將會產生追蹤訊息看起來如下所示：  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 如果您看到其中一個訊息，您需要逐步執行程式碼來判斷發生損毀。 若要找出更精確地說記憶體覆寫發生的位置，您可以進行明確呼叫`AfxCheckMemory`自己。 例如:   
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 如果第一個判斷提示會成功，而第二個失敗，則表示必須發生在兩個呼叫之間的函式中的記憶體覆寫。  
  
 根據您的應用程式的本質，您可能會發現`afxMemDF`導致您的程式執行測試的速度太慢。 `afxMemDF`變數會造成`AfxCheckMemory`針對每次呼叫新的呼叫，並刪除。 在此情況下，您應該散佈到呼叫`AfxCheckMemory`（），如上所示，然後再次嘗試找出記憶體覆寫該方法。  
  
## <a name="see-also"></a>請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)