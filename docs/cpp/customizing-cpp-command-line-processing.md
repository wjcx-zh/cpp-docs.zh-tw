---
title: 自訂 C++ 命令列處理
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857550"
---
# <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理

**Microsoft 專屬**

如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 此常式會 `_setargv` 呼叫，並在[萬用字元展開](../cpp/wildcard-expansion.md)中說明。 若要隱藏其使用方式，請定義不在包含 `main` 函式的檔案中執行任何工作的常式，並將其命名為 `_setargv`。 接著，`_setargv`的定義會滿足 `_setargv` 的呼叫，而且不會載入程式庫版本。

同樣地，如果您從未透過 `envp` 引數來存取環境資料表，您可以提供自己的空白常式來取代 `_setenvp`（環境處理常式）。 就像 `_setargv` 函數一樣，`_setenvp` 必須宣告為**extern "C"** 。

您的程式可能會呼叫 C 執行時間程式庫中的 `spawn` 或 `exec` 系列的常式。 如果是這種情況，您就不應該隱藏環境處理常式，因為這個常式會用來將環境從父處理序傳遞至子處理序。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[main：程式啟動](../cpp/main-program-startup.md)