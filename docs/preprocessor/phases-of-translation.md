---
title: 轉譯階段
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: d072c9aec48d815ba85f8a12576baa6447703f8c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218300"
---
# <a name="phases-of-translation"></a>轉譯階段

C 和 C++ 程式是由一個或多個原始程式檔所組成，每個原始程式檔會包含一些程式文字。 原始程式檔連同其*include*檔案、使用`#include`預處理器指示詞所包含的檔案, 但不包括條件式`#if`編譯指示詞 (例如) 所移除的程式碼區段, 稱為*轉譯單位*。

來源檔案可以在不同的時間轉譯。 事實上, 通常只會轉譯過期的檔案。 轉譯的轉譯單位可以處理為不同的目的檔或目的碼程式庫。 然後這些各自轉譯的轉譯單位會彼此連結，構成可執行程式或動態連結程式庫 (DLL)。 如需可做為連結器輸入之檔案的詳細資訊, 請參閱[連結輸入](../build/reference/link-input-files.md)檔。

轉譯單位可能使用下列方式進行通訊：

- 呼叫具有外部連結的函式。

- 呼叫具有外部連結的類別成員函式。

- 直接修改具有外部連結的物件。

- 直接修改檔案。

- 處理序間通訊 (只適用於 Microsoft Windows 應用程式)。

下列清單將描述編譯器轉譯檔案的各個階段：

*字元對應*\
原始程式檔中的字元會對應至內部來源表示。 在這個階段中，三併詞序列會轉換成單一字元的內部表示。

*行接合*\
以反斜線 ( **\\** ) 結尾的所有行, 後面緊接著分行符號, 會與原始程式檔中的下一行聯結, 以構成實體行的邏輯行。 除非原始程式檔是空的, 否則來源檔案必須以不是以反斜線開頭的分行符號結尾。

*Token 化*\
原始程式檔會分成前置處理語彙基元和空白字元。 原始程式檔中的每一個註解會分別取代為一個空白字元。 新行字元會加以保留。

*預處理*\
前置處理指示詞會執行，而且巨集會展開至原始程式檔。 `#include` 陳述式會在任何包含的文字上，叫用以上述三個轉譯步驟開始的轉譯。

*字元集對應*\
所有來源字元集成員和逸出序列都會轉換成它們在執行字元集中的相等用法。 在 Microsoft C 和 C++ 中，來源和執行字元集都是 ASCII。

*字串串連*\
所有相鄰字串和寬字串常值都會串連。 例如，`"String " "concatenation"` 會成為 `"String concatenation"`。

*機器翻譯*\
所有語彙基元都會經過語法和語意上的分析，而且這些語彙基元會轉換成目的碼。

*機械*\
所有外部參考都會加以解析，以建立可執行程式或動態連結程式庫。

編譯器會在遇到語法錯誤的轉譯階段發出警告或錯誤。

連結器會解析所有外部參考，並透過結合一個或多個分別處理的轉譯單位與標準程式庫建立可執行程式或 DLL。

## <a name="see-also"></a>另請參閱

[前置處理器](../preprocessor/preprocessor.md)
