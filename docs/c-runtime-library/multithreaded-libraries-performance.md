---
title: "多執行緒程式庫效能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 8eeadc61c41d37247b08bdc8e3806da6d6200e4a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="multithreaded-libraries-performance"></a>多執行緒程式庫效能
單一執行緒 CRT 已不再提供使用。 本主題會討論從多執行緒程式庫取得最大效能的方法。  
  
## <a name="maximizing-performance"></a>將效能最大化  
 多執行緒程式庫的效能已經受到改善，並非常接近已被取代之單一執行緒程式庫的效能。 針對那些需要更高效能的情況，現已提供數種新功能。  
  
-   獨立資料流鎖定可讓您鎖定資料流，然後使用可直接存取資料流的 [_nolock 函式](../c-runtime-library/nolock-functions.md)。 這可從重要迴圈中將鎖定的使用提至外面。  
  
-   個別執行緒的地區設定可降低多執行緒案例的地區設定存取成本 (請參閱 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md))。  
  
-   與地區設定相關的函式 (名稱以 _l 作為結尾) 會以參數的形式接受地區設定，以移除大量成本 (例如，[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md))。  
  
-   針對常用字碼頁的最佳化，可降低許多簡短作業的成本。  
  
-   定義 [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md)可強制所有 I/O 作業採用單一執行緒 I/O 模型，並使用函式的 _nolock 版本。 這可提供高度以 I/O 為基礎的單一執行緒應用程式，以取得更加的效能。  
  
-   公開 CRT 堆積控制代碼可讓您針對 CRT 堆積啟用 Windows 低分散堆積 (LFH)，這可以大幅提升高度調整案例的效能。  
  
## <a name="see-also"></a>另請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
