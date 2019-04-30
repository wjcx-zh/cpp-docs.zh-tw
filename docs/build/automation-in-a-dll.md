---
title: DLL 中的 Automation
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 4ac60c44348ea21f490cb312285ae88ac682cf7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341671"
---
# <a name="automation-in-a-dll"></a>DLL 中的 Automation

當您在 MFC DLL 精靈中選擇 [自動化] 選項時，精靈會提供您使用下列：

- 起始物件描述語言 (。ODL) 檔案

- Include 指示詞 Afxole.h 的 STDAFX.h 檔案中

- 實作`DllGetClassObject`函式，呼叫**AfxDllGetClassObject**函式

- 實作`DllCanUnloadNow`函式，呼叫**AfxDllCanUnloadNow**函式

- 實作`DllRegisterServer`函式，呼叫[登錄下列項目](../mfc/reference/coleobjectfactory-class.md#updateregistryall)函式

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [Automation 伺服程式](../mfc/automation-servers.md)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
