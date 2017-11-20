---
title: "結構 RUNTIME_FUNCTION |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 476ce4ad532f1e02b8863e2276fe0300c5895270
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="struct-runtimefunction"></a>struct RUNTIME_FUNCTION
以資料表為基礎的例外狀況處理的配置堆疊空間，或呼叫另一個函式 （例如，非分葉函式） 所有函式需要資料表項目。 函式表項目中的格式：  
  
|||  
|-|-|  
|ULONG|函式的起始位址|  
|ULONG|函式結束位址|  
|ULONG|回溯資訊位址|  
  
 RUNTIME_FUNCTION 結構必須是 DWORD 在記憶體中的對齊。 所有位址都都相對的映像，也就是從含有函式表格項目之影像的起始位址的 32 位元位移。 這些項目會進行排序，並放在 PE32 + 映像的.pdata 區段。 對於動態產生的函式 [JIT 編譯器]，執行階段支援這些函式必須使用 RtlInstallFunctionTableCallback 或 RtlAddFunctionTable 提供此資訊給作業系統。 若要這樣做會導致不可靠的例外狀況處理和偵錯的處理序。  
  
## <a name="see-also"></a>另請參閱  
 [回溯資料以進行例外狀況處理與偵錯工具支援](../build/unwind-data-for-exception-handling-debugger-support.md)