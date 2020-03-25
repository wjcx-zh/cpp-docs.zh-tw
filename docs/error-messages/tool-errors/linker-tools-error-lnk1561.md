---
title: 連結器工具錯誤 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194846"
---
# <a name="linker-tools-error-lnk1561"></a>連結器工具錯誤 LNK1561

必須定義進入點

連結器找不到*進入點*，也就是要在可執行檔中呼叫的初始函式。 根據預設，連結器會尋找主控台應用程式的 `main` 或 `wmain` 函式、Windows 應用程式的 `WinMain` 或 `wWinMain` 功能，或 `DllMain` 需要初始化的 DLL。 您可以使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項來指定另一個函數。

此錯誤可能有幾個原因：
- 您可能未在要連結的檔案清單中，包含定義您的進入點的檔案。 確認包含進入點函式的檔案已連結至您的應用程式。
- 您可能已使用錯誤的函數簽章定義進入點;例如，您可能拼錯或使用了函數名稱的錯誤大小寫，或指定的傳回類型或參數類型不正確。
- 建立 DLL 時，您可能未指定[/DLL](../../build/reference/dll-build-a-dll.md)選項。
- 當您使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項時，可能指定進入點函式的名稱不正確。
- 如果您使用[LIB](../../build/reference/lib-reference.md)工具來建立 DLL，您可能已指定 .def 檔案。 若是如此，請從組建中移除 .def 檔案。

建立應用程式時，連結器會尋找呼叫的進入點函式來啟動程式碼。 這是在應用程式載入並初始化執行時間之後所呼叫的函式。 您必須為應用程式提供進入點函式，否則您的應用程式將無法執行。 針對 DLL，進入點是選擇性的。 根據預設，連結器會尋找具有數個特定名稱和簽章之一的進入點函式，例如 `int main(int, char**)`。 您可以使用/ENTRY 連結器選項，指定另一個函式名稱做為進入點。

## <a name="example"></a>範例

下列範例會產生 LNK1561：

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
