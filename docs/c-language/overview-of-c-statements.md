---
title: C 陳述式概觀
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: bfa6840553055202f26f55e1dc5971bfd047b2de
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857069"
---
# <a name="overview-of-c-statements"></a>C 陳述式概觀

C 陳述式包含語彙基元、運算式和其他陳述式。 形成另一個陳述式元件的陳述式稱為封入陳述式的「主體」。 本節中討論由下列語法指定的每種陳述式類型。

## <a name="syntax"></a>語法

*statement*: [labeled-statement](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[expression-statement](../c-language/expression-statement-c.md)

[selection-statement](../c-language/if-statement-c.md)

[iteration-statement](../c-language/do-while-statement-c.md)

[jump-statement](../c-language/break-statement-c.md)

[try-except-語句](../c-language/try-except-statement-c.md)/* Microsoft 專有\*/

[try-catch-finally 語句](../c-language/try-finally-statement-c.md) / \* Microsoft 特有的\*/

通常陳述式的主體為一種「複合陳述式」。 複合陳述式包含其中可能內含關鍵字的其他陳述式。 複合陳述式以大括號 (**{ }**) 分隔。 所有其他 C 陳述式以分號 (**;**) 結束。 分號是陳述式結束字元。

運算陳述式內含一個 C 運算式，該運算式可包含在[運算式和指派](../c-language/expressions-and-assignments.md)中說明的算術或邏輯運算子。 Null 陳述式是一個空的陳述式。

所有 C 陳述式都可以使用包含名稱和冒號的識別標籤做為開頭。 因為只有 `goto` 陳述式會辨識陳述式標籤，因此將與 `goto` 一起討論陳述式標籤。 如需詳細資訊，請參閱 [goto 和標記陳述式](../c-language/goto-and-labeled-statements-c.md)。

## <a name="see-also"></a>請參閱

[陳述式](../c-language/statements-c.md)
