---
title: "-建構函式註解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25b6ebff4108b47e70b34aa6d83293bede78ee97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="-constructors-comment"></a>// 建構函式註解
`// Constructors` > 一節的 MFC 類別宣告會宣告建構函式 （在 c + + 意義），以及實際使用的物件所需的任何初始化函式。 例如，`CWnd::Create`是建構函式 > 一節中，因為當您使用`CWnd`物件，它必須 「 完整 」 來建構第一次呼叫 c + + 建構函式，然後再呼叫**建立**函式。 一般而言，這些成員是公用的。  
  
 例如，類別`CStdioFile`有三個建構函式，其中會顯示在下方列出[註解的範例](../mfc/an-example-of-the-comments.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [實作註解](../mfc/decrement-implementation-comment.md)   
 [屬性註解](../mfc/decrement-attributes-comment.md)   
 [作業註解](../mfc/decrement-operations-comment.md)   
 [可覆寫註解](../mfc/decrement-overridables-comment.md)

