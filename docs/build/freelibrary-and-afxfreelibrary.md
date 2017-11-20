---
title: "FreeLibrary 和 AfxFreeLibrary |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs: C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 276d93489a714dda5edd721c532c28c03b3ca41f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary
明確連結的 DLL 呼叫的處理序[FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)函式時不再需要 DLL 模組。 這個函式會遞減模組的參考計數，並參考計數為零，如果取消對應從處理序的位址空間。  
  
 MFC 應用程式中，使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而不是`FreeLibrary`卸載 MFC 擴充 DLL。 介面 （函式原型）`AfxFreeLibrary`相同`FreeLibrary`。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [如何以隱含方式連結到 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [決定要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual c + + 中的 Dll](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)