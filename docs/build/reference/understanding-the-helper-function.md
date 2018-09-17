---
title: 了解 Helper 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90ca214b28296417ab80341232c08a55b92adff4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725478"
---
# <a name="understanding-the-helper-function"></a>了解 Helper 函式

連結器支援延遲載入 helper 函式是什麼實際在執行階段載入 DLL。 您可以修改以自訂其行為，藉由撰寫自己的函式，並將其連結到您的程式，而不是使用提供的協助程式函式中 Delayimp.lib 協助程式函式。 一個 helper 函式是所有的延遲載入 Dll。

如果您想要進行匯入之 DLL 的名稱為基礎的特定處理，您可以提供自己的 helper 函式的版本。

Helper 函式會執行下列動作：

- 檢查是否已載入的程式庫來儲存的控制代碼

- 呼叫**LoadLibrary**嘗試載入的 dll

- 呼叫**GetProcAddress**嘗試取得程序的位址

- 延遲匯入傳回載入至呼叫目前已載入的進入點 thunk

Helper 函式可以回呼通知攔截在程式中每個下列動作：

- 當 helper 函式會啟動

- 前面**LoadLibrary**稱為協助程式函式

- 前面**GetProcAddress**稱為協助程式函式

- 如果在呼叫**LoadLibrary** helper 函式中失敗

- 如果在呼叫**GetProcAddress** helper 函式中失敗

- 完成後的協助程式函式處理

每一種攔截點可以傳回值，將會改變的協助程式常式，除了延遲匯入負載 thunk 傳回某種形式的正常處理。

預設的協助程式程式碼位於 Delayhlp.cpp 和 Delayimp.h （vc\include)，並編譯中 Delayimp.lib （在 vc\lib)。 您必須在編譯中包括此程式庫，除非您撰寫您自己的 helper 函式。

下列主題說明的協助程式函式：

- [Visual C++ 6.0 之後 DLL 延遲載入協助程式函式的變更](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [呼叫慣例、參數和傳回型別](../../build/reference/calling-conventions-parameters-and-return-type.md)

- [結構和常數定義](../../build/reference/structure-and-constant-definitions.md)

- [計算需要的值](../../build/reference/calculating-necessary-values.md)

- [卸載延遲載入的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)