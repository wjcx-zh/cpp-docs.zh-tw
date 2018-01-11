---
title: "C 執行階段程式庫函式的執行緒控制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49d3d9029f85a8a80da6a7cd38bb26b887223d35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-run-time-library-functions-for-thread-control"></a>執行緒控制的 C 執行階段程式庫函式
所有 Win32 程式都必須至少一個執行緒。 任何執行緒可以建立額外的執行緒。 執行緒可以快速完成其工作，然後結束，或它可以保持使用中程式的存留期間。  
  
 嵌入 LIBCMT 和 MSVCRT C 執行階段程式庫提供下列函式的執行緒建立和終止： [_beginthread、 _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)和[_endthread、 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。  
  
 `_beginthread`和`_beginthreadex`函式會建立新的執行緒，並傳回執行緒識別項，如果作業成功。 如果它已完成執行，或它可能會終止本身呼叫自動終止執行緒`_endthread`或`_endthreadex`。  
  
> [!NOTE]
>  如果您要從使用 Libcmt.lib 建立程式呼叫 C 執行階段常式，您必須啟動您的執行緒與`_beginthread`或`_beginthreadex`函式。 請勿使用 Win32 函式`ExitThread`和`CreateThread`。 使用`SuspendThread`時可能會導致死結多個執行緒遭到封鎖而等待 暫止的執行緒完成其存取權的 C 執行階段資料結構。  
  
##  <a name="_core_the__beginthread_function"></a>_Beginthread 和 _beginthreadex 函式  
 `_beginthread`和`_beginthreadex`函式會建立新的執行緒。 執行緒共用的程式碼和資料區段的處理程序與其他處理序中的執行緒，但有自己的唯一暫存器值、 堆疊空間和目前的指令位址。 系統會將 CPU 時間的每個執行緒，以便處理程序中的所有執行緒可以同時都執行。  
  
 `_beginthread`和`_beginthreadex`類似於[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) Win32 API 中的函式，但有這些差異：  
  
-   它們會初始化某些 C 執行階段程式庫的變數。 這很重要，只有當您使用 C 執行階段程式庫中您的執行緒。  
  
-   `CreateThread`有助於提供控制的安全性屬性。 若要啟動的執行緒處於暫停狀態，您可以使用此函式。  
  
 `_beginthread`和`_beginthreadex`至新的執行緒，如果成功或錯誤程式碼傳回的控制代碼，如果發生錯誤。  
  
##  <a name="_core_the__endthread_function"></a>_Endthread 和 _endthreadex 函式  
 [_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函式會結束執行緒，所建立`_beginthread`(同樣地，`_endthreadex`中止建立的執行緒`_beginthreadex`)。 當完成執行緒終止自動。 `_endthread`和`_endthreadex`可用於從執行緒內的條件式終止。 比方說，如果無法取得控制項的通訊埠，可以結束專門用於通訊處理的執行緒。  
  
## <a name="see-also"></a>請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)