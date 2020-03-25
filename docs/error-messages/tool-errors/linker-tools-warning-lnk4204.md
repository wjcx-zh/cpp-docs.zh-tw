---
title: 連結器工具警告 LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 98c53c9b998e9bd544c1cc72bd2b0c3fd2b0a418
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193858"
---
# <a name="linker-tools-warning-lnk4204"></a>連結器工具警告 LNK4204

' filename ' 缺少參考模組的偵錯工具資訊;連結化物件，如同沒有任何調試資訊

.Pdb 檔案有錯誤的簽章。 連結器將會繼續連結化物件，而不會有任何 debug 資訊。 您可能想要使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)選項重新編譯物件檔案。

如果程式庫中的某些物件參考已不存在的檔案，就會發生 LNK4204。 這可能會在重建解決方案時發生，例如。因為發生編譯錯誤，所以可能會刪除或不重建物件檔案。 在此情況下，您可以使用 **/Z7**或 **/fd**來進行編譯，以更新物件來參考每個程式庫的單一檔案（不是預設的 .pdb 檔案名）。  如需詳細資訊，請參閱 [/Fd (程式資料庫檔名)](../../build/reference/fd-program-database-file-name.md)。  請確定在原始檔控制系統中每次更新時，會將 .pdb 與程式庫一併儲存。
