---
title: 原始程式檔和來源程式
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: 4562f8397e9d2d3e044086b8da8d56ba25047ebd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152530"
---
# <a name="source-files-and-source-programs"></a>原始程式檔和來源程式

一個原始程式可分成一個或多個「原始程式檔」或「轉譯單位」。 輸入到編譯器者稱為「轉譯單位」。

## <a name="syntax"></a>語法

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*

[宣告概觀](../c-language/overview-of-declarations.md)說明 `declaration` 非終端項的語法，而《前置處理器參考》則說明如何處理[轉譯單位](../preprocessor/phases-of-translation.md)。

> [!NOTE]
>  如需 ANSI 語法慣例的說明，請參閱 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)的簡介。

轉譯單位的元件包含函式定義和識別項宣告的外部宣告。 這些宣告和定義可以存在於原始程式檔、標頭檔、程式庫和其他程式所需的檔案中。 您必須編譯每一個轉譯單位，並連結產生的目的檔，以便建置程式。

C「原始程式」為指示詞、pragma、宣告、定義、陳述式區塊和函式的集合。 若要成為 Microsoft C 程式的有效元件，每一個都必須使用本書所描述的語法，不過，它們在程式中可以任何順序顯示 (受到於本書所述規則的影響)。 不過，這些元件在程式中的位置會影響在程式中使用變數和函式的方式。 (如需詳細資訊，請參閱[存留期、範圍、可視性和連結](../c-language/lifetime-scope-visibility-and-linkage.md))。

原始程式檔不需要包含可執行的陳述式。 例如，將變數的定義放在某個原始程式檔中，再於使用這些變數的其他原始程式檔中宣告這些變數的參考，可能會對您有幫助。 這項技術在必要時可讓您更容易尋找及更新定義。 基於相同原因，常數和巨集通常會組織為稱為「Include 檔」或「標頭檔」的檔案，這些檔案可在原始程式檔中視需要加以參考。 如需[巨集](../preprocessor/macros-c-cpp.md)和 [include 檔](../preprocessor/hash-include-directive-c-cpp.md)的詳細資訊，請參閱《前置處理器參考》。

## <a name="see-also"></a>另請參閱

[程式結構](../c-language/program-structure.md)
