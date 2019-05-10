---
title: DLL 中的 Automation
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220927"
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

[建立 C /C++在 Visual Studio 中的 Dll](dlls-in-visual-cpp.md)
