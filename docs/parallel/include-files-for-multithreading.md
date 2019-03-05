---
title: 多執行緒的 Include 檔
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: 79b5c56eecfaf28743eec4ba6b4cee56156d6e2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257419"
---
# <a name="include-files-for-multithreading"></a>多執行緒的 Include 檔

標準 include 檔案的程式庫中實作宣告 C 執行階段程式庫函式。 如果您使用[完全最佳化](../build/reference/ox-full-optimization.md)(/ Ox) 或[fastcall 呼叫慣例](../build/reference/gd-gr-gv-gz-calling-convention.md)(/ Gr) 選項，編譯器會假設所有函式都應該使用的暫存器呼叫慣例。 使用 C 呼叫慣例，編譯的執行階段程式庫函式和標準 include 檔案中的宣告會告知編譯器產生正確的外部參考，這些函式。

## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)
