---
title: 包含檔案的多執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62b94f4a7a394b78cb7c6f23275709e4aeacc774
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="include-files-for-multithreading"></a>多執行緒的 Include 檔
標準 include 檔的文件庫中實作時，宣告 C 執行階段程式庫函式。 如果您使用[完全最佳化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 呼叫慣例](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 選項，編譯器會假設所有函數都應該使用暫存器呼叫慣例。 執行階段程式庫函式已使用的 C 呼叫慣例，在編譯和標準 include 檔案中的宣告會告訴編譯器產生正確的外部參考，這些函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)