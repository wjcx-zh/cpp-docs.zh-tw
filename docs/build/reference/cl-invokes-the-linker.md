---
title: CL 叫用連結器
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: 1f9bb466ae89b8e3491b027a98b28935e7c8b523
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440189"
---
# <a name="cl-invokes-the-linker"></a>CL 叫用連結器

除非使用/c 選項，否則 CL 會在編譯之後自動叫用連結器。 CL 會將編譯期間建立的 .obj 檔案名稱，以及在命令列上指定的任何其他檔案名稱傳遞給連結器。 連結器會使用連結環境變數中所列的選項。 您可以使用/link 選項，在 CL 命令列上指定連結器選項。 遵循/link 選項的選項會覆寫連結環境變數中的選項。 下表中的選項會隱藏連結。

|選項|描述|
|------------|-----------------|
|/c|編譯而不連結|
|/E、/EP、/P|前置處理而不編譯或連結|
|/Zg|產生函數原型|
|/Zs|檢查語法|

如需連結的詳細資訊，請參閱[MSVC 連結器選項](linker-options.md)。

## <a name="example"></a>範例

假設您正在編譯三個 C 原始程式檔： MAIN. c、MOD1 和 MOD2。 每個檔案都包含呼叫不同檔案中定義的函數：

- MAIN. c 會呼叫 MOD1 中的函式 `func1`，而函式 `func2` 在 MOD2 中。

- MOD1 會呼叫標準程式庫函數 `printf_s` 和 `scanf_s`。

- MOD2 會呼叫名為 `myline` 和 `mycircle`的圖形函式，這些函式定義于名為 MYGRAPH 的程式庫中。

若要建立此程式，請使用下列命令列進行編譯：

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL 會先編譯 C 來源檔案，並建立物件檔案 MAIN、MOD1 和 MOD2。編譯器會將標準程式庫的名稱放在每個 .obj 檔案中。 如需詳細資訊，請參閱[使用執行時間程式庫](md-mt-ld-use-run-time-library.md)。

CL 會將 .obj 檔案的名稱連同名稱 MYGRAPH 傳遞至連結器。 連結器會解析外部參考，如下所示：

1. 在 MAIN .obj 中，會使用 MOD1 中的定義來解析 `func1` 的參考。`func2` 的參考是使用 MOD2 中的定義來解析。

1. 在 MOD1 中，`printf_s` 和 `scanf_s` 的參考會使用程式庫中的定義來解析，而程式庫會在 MOD1 中找到名稱。

1. 在 MOD2 中，`myline` 和 `mycircle` 的參考會使用 MYGRAPH 中的定義來解析。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[設定編譯器選項](compiler-command-line-syntax.md)
