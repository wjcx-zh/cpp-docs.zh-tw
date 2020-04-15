---
title: 連結器工具錯誤 LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357755"
---
# <a name="linker-tools-error-lnk1561"></a>連結器工具錯誤 LNK1561

必須定義的點

連結器沒有找到*入口點*,這是呼叫您的可執行檔的初始函數。 默認情況下,連結程式查找控制台應用、Windows `main` `wmain``WinMain`應用`wWinMain`或功能`DllMain`或需要初始化的 DLL 的或函數。 您可以使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項指定其他函數。

錯誤可能有多種原因:

- 您可能沒有在要連結的檔案清單中包括定義入口點的檔案。 驗證包含入口點功能的檔是否連結到你的應用。
- 您可能使用錯誤的函數簽名定義了入口點;但是,使用簽名定義了入口點。例如,您可能拼錯了或使用了函數名稱的錯誤大小寫,或者錯誤地指定了返回類型或參數類型。
- 生成 DLL 時,您可能沒有指定[/DLL](../../build/reference/dll-build-a-dll.md)選項。
- 使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項時,可能錯誤地指定了入口點函數的名稱。
- 如果使用[LIB](../../build/reference/lib-reference.md)工具生成 DLL,則可能已指定 .def 檔案。 如果是這樣,請從生成中刪除 .def 檔。

構建應用時,連結器將查找要調用的入口點函數以啟動代碼。 這是載入應用並初始化運行時後調用的函數。 您必須為應用提供入口點功能,否則你的應用無法運行。 對於 DLL,入口點是可選的。 預設情況下,連結器搜尋有多個特定名稱和簽名之一的入口點函數,例如`int main(int, char**)`。 您可以使用 /ENTRY 連結器選項指定其他函數名稱作為入口點。

## <a name="example"></a>範例

以下範例生成 LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
