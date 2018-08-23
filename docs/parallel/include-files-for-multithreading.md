---
title: 包含的檔案進行多執行緒處理 |Microsoft Docs
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
ms.openlocfilehash: 73444c72878073d881abec08c474eb1f1ce64f02
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2018
ms.locfileid: "42540969"
---
# <a name="include-files-for-multithreading"></a>多執行緒的 Include 檔
標準 include 檔案的程式庫中實作宣告 C 執行階段程式庫函式。 如果您使用[完全最佳化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 呼叫慣例](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 選項，編譯器會假設所有函式都應該使用的暫存器呼叫慣例。 使用 C 呼叫慣例，編譯的執行階段程式庫函式和標準 include 檔案中的宣告會告知編譯器產生正確的外部參考，這些函式。  
  
## <a name="see-also"></a>另請參閱  

[使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)