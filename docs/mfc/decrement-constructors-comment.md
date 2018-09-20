---
title: -建構函式註解 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03a65c3f870b1e7648f03b70efe7242c35a21f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429350"
---
# <a name="-constructors-comment"></a>// 建構函式註解

`// Constructors`區段的 MFC 類別宣告會宣告建構函式 （在 c + +），以及真正使用的物件所需的任何初始化函式。 例如，`CWnd::Create`是在建構函式區段中，因為使用之前`CWnd`物件，它必須"完全建構 「 第一次呼叫 c + + 建構函式，然後呼叫`Create`函式。 一般而言，這些成員是公用的。

例如，類別`CStdioFile`有三個建構函式，其中會顯示在清單中，在[註解的範例](../mfc/an-example-of-the-comments.md)。

## <a name="see-also"></a>另請參閱

[使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)<br/>
[實作註解](../mfc/decrement-implementation-comment.md)<br/>
[屬性註解](../mfc/decrement-attributes-comment.md)<br/>
[作業註解](../mfc/decrement-operations-comment.md)<br/>
[可覆寫註解](../mfc/decrement-overridables-comment.md)

