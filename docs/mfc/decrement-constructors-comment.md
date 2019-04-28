---
title: -建構函式註解
ms.date: 11/04/2016
helpviewer_keywords:
- constructors comment
- declarations, constructors
- MFC source files, Constructors comment
- declaring constructors, code comments
- comments, MFC
- comments, constructors comment
- constructors [MFC], declaring
- instance constructors, code comments
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
ms.openlocfilehash: e0d02af016a0c7bfb0869b7cdd30fe0db2975102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240857"
---
# <a name="-constructors-comment"></a>// 建構函式註解

`// Constructors`一節的 MFC 類別宣告會宣告建構函式 (在C++意義)，才能真正使用物件以及任何初始化函式。 例如，`CWnd::Create`是在建構函式區段中，因為使用之前`CWnd`物件，它必須 」 完全建構 「 第一個呼叫C++建構函式，然後呼叫`Create`函式。 一般而言，這些成員是公用的。

例如，類別`CStdioFile`有三個建構函式，其中會顯示在清單中，在[註解的範例](../mfc/an-example-of-the-comments.md)。

## <a name="see-also"></a>另請參閱

[使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)<br/>
[實作註解](../mfc/decrement-implementation-comment.md)<br/>
[屬性註解](../mfc/decrement-attributes-comment.md)<br/>
[作業註解](../mfc/decrement-operations-comment.md)<br/>
[可覆寫註解](../mfc/decrement-overridables-comment.md)
