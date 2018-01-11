---
title: "C++ 標準程式庫中的執行緒安全 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fa4c69e79a918d7b8cf77e03f76c81e846d5a5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="thread-safety-in-the-c-standard-library"></a>C++ 標準程式庫中的執行緒安全
下列執行緒安全性規則適用於 C++ 標準程式庫中的所有類別 (這包括 `shared_ptr`)，如下所述。  有時會提供較強的保證，例如，標準 iostream 物件 (如下所述)，以及特別用來進行多執行緒處理的類型 (如 [\<atomic>](../standard-library/atomic.md) 中的類型)。  
  
 物件為安全執行緒，可供從多個執行緒讀取。 例如，提供物件 A，則可以安全地同時從執行緒 1 和執行緒 2 讀取 A。  
  
 如果某個執行緒正在寫入物件，則必須保護相同或其他執行緒上，對該物件進行的所有讀取和寫入。 例如，提供物件 A 時，如果執行緒 1 正在寫入至 A，則必須防止執行緒 2 讀取或寫入至 A。  
  
 您可以安全地讀取和寫入至某個類型的一個執行個體，即使另一個執行緒正在讀取或寫入至相同類型的不同執行個體也是一樣。 例如，提供相同類型的物件 A 和 B，則正在執行緒 1 中寫入 A，且正在執行緒 2 中讀取 B 時是安全的。  
  
## <a name="sharedptr"></a>shared_ptr  
 多個執行緒可以同時讀取和寫入不同的 [shared_ptr](../standard-library/shared-ptr-class.md) 物件，即使當物件是共用擁有權的複本時也是一樣。  
  
## <a name="iostream"></a>iostream  
 標準 iostream 物件 `cin`、`cout`、`cerr`、`clog`、`wcin`、`wcout`、`wcerr` 和 `wclog` 遵循與其他類別相同的規則，但有例外：可以從多個執行緒安全地寫入至物件。 例如，執行緒 1 可以與執行緒 2 同時寫入 [cout](../standard-library/iostream.md#cout)。 不過，這可能會導致混合來自兩個執行緒的輸出。  
  
> [!NOTE]
>  從資料流緩衝區中讀取，不視為讀取作業。 而是視為寫入作業，因為類別的狀態已變更。  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)



