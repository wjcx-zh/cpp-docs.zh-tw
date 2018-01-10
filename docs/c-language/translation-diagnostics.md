---
title: "轉譯：診斷 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10349357fa0411357b702ff48ff9407c1f5b91e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="translation-diagnostics"></a>轉譯：診斷
**ANSI 2.1.1.3** 如何識別診斷  
  
 Microsoft C 會產生下列格式的錯誤訊息：  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 其中 *filename* 是發生錯誤所在的原始程式檔名稱，*line-number* 是編譯器偵測到錯誤的行號，`diagnostic` 是「錯誤」或「警告」，`number` 是用於識別錯誤或警告的唯一四位數字 (前面加上 **C**，如語法中所註解)，而 `message` 是說明訊息。  
  
## <a name="see-also"></a>請參閱  
 [實作定義的行為](../c-language/implementation-defined-behavior.md)