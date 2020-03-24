---
title: 嚴重錯誤 C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 649686857000b2bee469f0e3ec551d49717c1d7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204070"
---
# <a name="fatal-error-c1084"></a>嚴重錯誤 C1084

無法閱讀 filetype 檔案：'file' : 訊息

此錯誤通常因編譯器呼叫內部系統 API 失敗所導致。 遇到此錯誤時所顯示的訊息通常是由[_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)或[FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)所產生。

執行下列步驟，可能有助於解決 C1084：

- 確保指定的檔案存在。

- 確保設定適當的權限，以存取指定的檔案。

- 請確定命令列語法遵守[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)底下所述的規則。

- 請確定已正確設定環境變數**TMP**和**TEMP** ，以及適當的許可權，以便存取這些環境變數所參考的目錄。 此外，請確定**TMP**和**TEMP**環境變數所參考的磁片磁碟機包含足夠的可用空間量。

- 如果訊息指出「錯誤的檔案號碼」，則指定的檔案可能已在前景關閉，而在背景編譯。

在執行上述診斷之後，執行清除組建。
