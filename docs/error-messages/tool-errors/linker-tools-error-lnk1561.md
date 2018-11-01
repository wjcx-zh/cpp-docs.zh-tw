---
title: 連結器工具錯誤 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: ad216c7b7a09b8dd5d2ca2b86bc3a386fa18a552
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552811"
---
# <a name="linker-tools-error-lnk1561"></a>連結器工具錯誤 LNK1561

必須定義進入點

找不到連結器*進入點*，初始的函式呼叫中可執行檔。 根據預設，連結器會尋找`main`或`wmain`主控台應用程式中，函式`WinMain`或`wWinMain`是 Windows 應用程式中，函式或`DllMain`隸屬於需要初始化的 dll。 您可以使用來指定另一個函式[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。

此錯誤有幾個原因：
- 您可能不包含在要連結的檔案清單中定義的進入點的檔案。 請確認包含進入點函式的檔案會連結到您的應用程式。
- 您定義使用錯誤的函式簽章; 進入點比方說，您可能有拼字錯誤或用於大小寫的函式名稱，或未正確指定傳回型別或參數類型。
- 您可能不會指定[/DLL](../../build/reference/dll-build-a-dll.md)選項建置 DLL 時。
- 您指定可能的進入點函式名稱不正確地使用時[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。
- 如果您使用[LIB](../../build/reference/lib-reference.md)工具來建立 DLL，您指定一個.def 檔案。 如果是的話，請從組建中移除.def 檔。

建置應用程式，當連結器會尋找進入點函式來呼叫，以啟動您的程式碼。 這是應用程式載入和執行階段初始化之後呼叫的函式。 您必須提供進入點函式應用程式，或您的應用程式無法執行。 進入點是選用的 dll。 根據預設，連結器會尋找進入點函式的其中幾個特定名稱和簽章，例如`int main(int, char**)`。 您可以指定另一個函式名稱的項目點使用 /ENTRY 連結器選項。

## <a name="example"></a>範例

下列範例會產生 LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```