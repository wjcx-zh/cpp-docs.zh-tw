---
title: "-作業的註解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Operations comment in MFC source files
- comments, MFC
- MFC source files, Operations comments
ms.assetid: f3bff48d-26be-4db6-8435-9e4d079838c9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 63b3d7a313f0f725444ba77612d8b53280393640
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="-operations-comment"></a>// 作業註解
`// Operations` MFC 類別宣告區段包含您可以在要讓它執行動作，或執行的動作 （執行作業） 的物件上呼叫成員函式。 這些函式是通常非**const**因為它們通常會有副作用。 它們可能是虛擬或虛擬根據類別的需求而定。 一般而言，這些成員是公用的。  
  
 中的範例清單裡類別`CStdioFile`，請在[註解的範例](../mfc/an-example-of-the-comments.md)，這份清單包括在這個註解的兩個成員函式：`ReadString`和`WriteString`。  
  
 與屬性一樣作業可以進一步細分。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [實作註解](../mfc/decrement-implementation-comment.md)   
 [建構函式註解](../mfc/decrement-constructors-comment.md)   
 [屬性註解](../mfc/decrement-attributes-comment.md)   
 [可覆寫註解](../mfc/decrement-overridables-comment.md)

