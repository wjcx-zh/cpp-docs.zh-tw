---
title: 連結器工具警告 LNK4049
ms.date: 11/04/2016
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: f9e5f1d9d5628a0da49300f541a4d5d4ce321c5f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024487"
---
# <a name="linker-tools-warning-lnk4049"></a>連結器工具警告 LNK4049

本機定義的符號 'symbol' 匯入

同時從匯出和匯入程式符號。

當您使用宣告的符號連結器便會產生這個警告`__declspec(dllexport)`儲存類別屬性中某個物件檔，並使用參考`__declspec(dllimport)`中另一個屬性。

警告 LNK4049 是更一般的版本[連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)。 當它無法判斷哪一個函式從參考匯入的符號時，連結器就會產生警告 LNK4049。

常見的案例而不是 LNK4217 產生 LNK4049 的位置如下：

- 執行所使用的累加連結[/incremental](../../build/reference/incremental-link-incrementally.md)選項。

- 使用執行整個程式最佳化[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)選項。

若要解決 LNK4049，請嘗試下列其中一項：

- 移除`__declspec(dllimport)`名稱從觸發 LNK4049 符號的向前宣告的宣告。 您可以使用搜尋二進位映像中的符號**DUMPBIN**公用程式。 **DUMPBIN/符號**參數可顯示 COFF 符號表中的映像。 如需詳細資訊**DUMPBIN**公用程式，請參閱[DUMPBIN 參考](../../build/reference/dumpbin-reference.md)。

- 暫時停用累加連結和整個程式最佳化。 重新編譯應用程式將會產生警告 LNK4217，其中包含要從中匯入的符號參考函式的名稱。 移除`__declspec(dllimport)`宣告從匯入的符號和啟用累加連結或所需的整個程式最佳化。

雖然最終產生的程式碼會正常運作，以呼叫匯入的函式所產生的程式碼是效率比直接呼叫函式。 當您使用選項編譯時，不會出現此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

如需詳細資訊匯入和匯出資料宣告，請參閱 < [dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>範例

連結下列兩個模組，將會產生 LNK4049。 第一個模組會產生包含單一的匯出函式的物件檔案。

```
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

## <a name="example"></a>範例

第二個模組會產生包含匯出的第一個模組，以及呼叫此函式內的函式的向前宣告的物件檔案`main`函式。 連結的第一個模組使用此模組會產生 LNK4049。 移除`__declspec(dllimport)`宣告將會解決這個警告。

```
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

[連結器工具警告 LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)