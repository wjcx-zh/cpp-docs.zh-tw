---
title: 萬用字元展開
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857173"
---
# <a name="wildcard-expansion"></a>萬用字元展開

**Microsoft 專屬**

您可以在命令列上使用問號 (?) 和星號 (*) 等萬用字元來指定檔案名稱和路徑引數。

命令列引數是由稱為 `_setargv` 的常式（或寬字元環境中的 `_wsetargv`）處理，預設不會將萬用字元展開為 `argv` 字串陣列中的個別字串。 如需啟用萬用字元展開的詳細資訊，請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[main：程式啟動](../cpp/main-program-startup.md)