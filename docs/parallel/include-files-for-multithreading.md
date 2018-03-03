---
title: "包含檔案的多執行緒 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f71b52bca5f636d80f2d55cc5e9ffc3e217d90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="include-files-for-multithreading"></a>多執行緒的 Include 檔
標準 include 檔的文件庫中實作時，宣告 C 執行階段程式庫函式。 如果您使用[完全最佳化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 呼叫慣例](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 選項，編譯器會假設所有函數都應該使用暫存器呼叫慣例。 執行階段程式庫函式已使用的 C 呼叫慣例，在編譯和標準 include 檔案中的宣告會告訴編譯器產生正確的外部參考，這些函式。  
  
## <a name="see-also"></a>請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)