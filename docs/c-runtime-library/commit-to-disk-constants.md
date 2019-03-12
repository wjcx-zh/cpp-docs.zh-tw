---
title: 認可到磁碟常數
ms.date: 11/04/2016
f1_keywords:
- vc.constants
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
ms.openlocfilehash: c02b18e5a4a731957a7c74cc45e6e181fe23fad8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750607"
---
# <a name="commit-to-disk-constants"></a>認可到磁碟常數

**Microsoft 專屬**

## <a name="syntax"></a>語法

```
#include <stdio.h>
```

## <a name="remarks"></a>備註

這些 Microsoft 特定的常數，會指定是否要將與開啟檔案相關聯的緩衝區排清至作業系統緩衝區或磁碟。 該模式會包含在指定讀取/寫入存取類型的字串中 (**"r"**、**"w"**、**"a"**、**"r+"**、**"w+"**、**"a+"**)。

認可到磁碟模式如下所列：

- **C**

   將指定緩衝區的未撰寫內容寫入磁碟。 此認可到磁碟功能只會在對 [fflush](../c-runtime-library/reference/fflush.md) 或 [_flushall](../c-runtime-library/reference/flushall.md) 函式做出明確呼叫時發生。 此模式在處理敏感性資料時非常有用。 例如，如果程式在呼叫 `fflush` 或 `_flushall` 之後終止，則可以確定您的資料已抵達作業系統的緩衝區。 不過，在作業系統也終止的情況下，除非檔案是以 **c** 選項開啟，否則該資料可能永遠都不會抵達磁碟。

- **n**

   將指定緩衝區的未撰寫內容寫入作業系統的緩衝區。 作業系統可以快取資料，然後判斷寫入磁碟的最佳時間。 在許多情況下，此行為將會是很有效率的程式行為。 不過，如果資料的保留非常重要 (例如銀行交易或機票資訊)，請考慮使用 **c** 選項。 預設是 **n** 模式。

> [!NOTE]
> **c** 與 **n** 選項並非 `fopen` 的 ANSI 標準之一部分，而是 Microsoft 延伸模組，但在需要 ANSI 可攜性時不應使用。

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>搭配現有程式碼使用認可到磁碟功能

根據預設，針對 [fflush](../c-runtime-library/reference/fflush.md) 或 [_flushall](../c-runtime-library/reference/flushall.md) 程式庫函式的呼叫，會將資料寫入由作業系統維護的緩衝區。 作業系統會判斷實際將資料寫入磁碟的最佳時間。 執行階段程式庫的認可到磁碟功能可讓您確保重要資料會直接寫入至磁碟，而不是寫入作業系統的緩衝區。 您可以透過將現有程式的物件檔案與 COMMODE.OBJ 連結，在不用重新撰寫該程式的情況下將此功能提供給它。

在產生的可執行檔中，對 `fflush` 的呼叫會將緩衝區的內容直接寫入磁碟，而對 `_flushall` 的呼叫則會將所有緩衝區的內容寫入磁碟。 這兩個函式是唯一會受到 COMMODE.OBJ 影響的函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[資料流 I/O](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)
