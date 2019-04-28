---
title: --作業註解
ms.date: 11/04/2016
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
ms.openlocfilehash: 7e4d0549d3d77916df532f105dc58ed9e9f78af2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240596"
---
# <a name="-operations-comment"></a>// 作業註解

`// Operations` MFC 類別宣告區段包含您可以呼叫物件，讓它執行動作，或執行的動作 （執行作業） 的成員函式。 這些函式是通常非**const**因為它們通常會有副作用。 它們可能是虛擬的或非虛擬根據類別的需求。 一般而言，這些成員是公用的。

中的範例清單類別`CStdioFile`，請在[註解的範例](../mfc/an-example-of-the-comments.md)，此清單包含此註解下的兩個成員函式：`ReadString`和`WriteString`。

如同屬性，可以進一步細分作業。

## <a name="see-also"></a>另請參閱

[使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)<br/>
[註解的範例](../mfc/an-example-of-the-comments.md)<br/>
[實作註解](../mfc/decrement-implementation-comment.md)<br/>
[建構函式註解](../mfc/decrement-constructors-comment.md)<br/>
[屬性註解](../mfc/decrement-attributes-comment.md)<br/>
[可覆寫註解](../mfc/decrement-overridables-comment.md)
