---
title: 連結器工具警告 LNK4049
ms.date: 04/09/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: 357bf5a981dddadfd79d2d6981ccc9c478909097
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477349"
---
# <a name="linker-tools-warning-lnk4049"></a>連結器工具警告 LNK4049

> 符號 '*符號*'中所定義的'*filename.obj*' 匯入

同時從匯出和匯入程式符號。

當您在某個物件檔中定義符號，並使用參考連結器便會產生這個警告`__declspec(dllimport)`宣告修飾詞，在另一個。

警告 LNK4049 是更一般的版本[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md)。 連結器會產生警告 LNK4049 時它無法判斷哪一個函式或物件參考檔案匯入的符號。

常見的案例而不是 LNK4217 產生 LNK4049 的位置如下：

- 使用時[/incremental](../../build/reference/incremental-link-incrementally.md)選項。

- 使用時[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)選項。

若要解決 LNK4049，請嘗試下列程序的其中一個：

- 移除`__declspec(dllimport)`觸發 LNK4049 符號的向前宣告修飾詞。 您可以使用搜尋二進位映像中的符號**DUMPBIN**公用程式。 **DUMPBIN /SYMBOLS**參數可顯示 COFF 符號表中的映像。 如需詳細資訊**DUMPBIN**公用程式，請參閱[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)。

- 暫時停用累加連結和整個程式最佳化。 重新編譯，則應用程式會產生警告 LNK4217，其中包含函式會參考匯入的符號名稱。 移除`__declspec(dllimport)`宣告修飾詞，從匯入的符號和重新啟用累加連結或所需的整個程式最佳化。

雖然最終產生的程式碼會正確運作，以呼叫匯入的函式所產生的程式碼是效率比直接呼叫函式。 當您使用編譯時，不會出現這個警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。

如需詳細資訊匯入和匯出資料宣告，請參閱 < [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>範例

連結下列兩個模組，將會產生 LNK4049。 第一個模組會產生包含單一的匯出函式的物件檔案。

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

第二個模組會產生包含匯出的第一個模組，以及呼叫此函式內的函式的向前宣告的物件檔案`main`函式。 連結的第一個模組使用此模組會產生 LNK4049。 移除`__declspec(dllimport)`修飾詞宣告，以解決這個警告。

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>另請參閱

[連結器工具警告 LNK4217](linker-tools-warning-lnk4217.md) \
[連結器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)