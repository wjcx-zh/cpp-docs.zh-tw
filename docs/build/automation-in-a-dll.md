---
title: DLL 中的 Automation
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220927"
---
# <a name="automation-in-a-dll"></a>DLL 中的 Automation

當您選擇 MFC DLL Wizard 中的 [自動化] 選項時，嚮導會提供下列內容：

- 入門物件描述語言（。ODL）檔案

- Afxole 之 STDAFX.H 檔中的 include 指示詞

- 函式的執行`DllGetClassObject` ，它會呼叫**AfxDllGetClassObject**函數

- 函式的執行`DllCanUnloadNow` ，它會呼叫**AfxDllCanUnloadNow**函數

- 函式的執行`DllRegisterServer` ，它會呼叫[COleObjectFactory：： UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall)函數

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [Automation 伺服程式](../mfc/automation-servers.md)

## <a name="see-also"></a>請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
