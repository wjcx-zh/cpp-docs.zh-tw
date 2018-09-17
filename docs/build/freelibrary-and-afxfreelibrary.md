---
title: FreeLibrary 和 AfxFreeLibrary |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs:
- C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e6c7e498100a60a3d4c592c343cc86b5ee0a0ea
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713358"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary

明確連結至 DLL 呼叫的程序[FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)函式時不再需要 DLL 模組。 這個函式模組的參考計數會遞減，並參考計數為零，如果取消從處理序位址空間。

在 MFC 應用程式中，使用[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)而不是`FreeLibrary`卸載 MFC 擴充 DLL。 介面 （函式原型），如`AfxFreeLibrary`等同於`FreeLibrary`。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [如何以隱含方式連結至 DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [判斷要使用哪一個連結方法](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)<br/>
[FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)