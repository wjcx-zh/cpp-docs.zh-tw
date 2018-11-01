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
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582685"
---
# <a name="customizing-c-command-line-processing"></a>自訂 C++ 命令列處理

## <a name="microsoft-specific"></a>Microsoft 特定的

如果您的程式不接受命令列引數，您可以隱藏執行命令列處理的程式庫常式用法，藉此稍微節省空間。 這個常式稱為`_setargv`述[萬用字元展開](../cpp/wildcard-expansion.md)。 若要隱藏其用途，定義 沒有任何作用中檔案包含的常式`main`函式，並將它命名`_setargv`。 在呼叫`_setargv`再經定義`_setargv`，且不會載入程式庫版本。

同樣地，如果您從未存取環境資料表，透過`envp`引數，您可以提供您自己空的常式以取代`_setenvp`，環境處理常式。 正如同`_setargv`函式`_setenvp`必須宣告為**extern"C"**。

您的程式可能會呼叫`spawn`或`exec`系列 C 執行階段程式庫中的常式。 如果是這種情況，您就不應該隱藏環境處理常式，因為這個常式會用來將環境從父處理序傳遞至子處理序。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[main：程式啟動](../cpp/main-program-startup.md)