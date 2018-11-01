---
title: CL 叫用連結器
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: e071209bd09fea17082379bf3f2486866b52c548
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447199"
---
# <a name="cl-invokes-the-linker"></a>CL 叫用連結器

CL 自動叫用編譯除非使用 /c 選項之後的連結器。 編譯期間建立的.obj 檔案的名稱以及任何其他命令列上指定的檔案名稱，CL 會傳遞至連結器。 連結器會使用連結的環境變數中所列的選項。 您可以使用 /link 選項指定 CL 命令列上的連結器選項。 請遵循 /link 選項的選項會覆寫 LINK 環境變數中。 下表中的選項會抑制連結。

|選項|描述|
|------------|-----------------|
|/c|編譯而不要連結|
|/ E，/EP，/P|前置處理，而不編譯或連結|
|/Zg|產生函式原型|
|/Zs|請檢查語法|

如需連結的進一步詳細資訊，請參閱 <<c0> [ 連結器選項](../../build/reference/linker-options.md)。

## <a name="example"></a>範例

假設您正在編譯三個 C 原始程式檔： MAIN.c、 MOD1.c 和 MOD2.c。 每個檔案包含定義另一個檔案中的函式呼叫：

- MAIN.c 呼叫函式`func1`MOD1.c 和函式中`func2`MOD2.c 中。

- MOD1.c 呼叫標準程式庫函式`printf_s`和`scanf_s`。

- MOD2.c 呼叫名為 「 圖形 」 函式`myline`和`mycircle`，定義名為 MYGRAPH.lib 文件庫中。

若要建置此程式，請使用下列的命令列編譯：

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL 第一次會編譯 C 原始程式檔，並建立 MAIN.obj、 MOD1.obj 和 MOD2.obj 物件檔案。編譯器會置於每個.obj 檔案中的標準程式庫的名稱。 如需詳細資訊，請參閱 <<c0> [ 使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)。

CL 傳遞.obj 檔案，以及名稱 MYGRAPH.lib，名稱為連結器。 連結器會解析外部參考，如下所示：

1. MAIN.obj，參考中`func1`MOD1.obj; 中使用的定義進行解析的參考`func2`MOD2.obj 中使用的定義進行解析。

1. 中的參考，MOD1.obj`printf_s`和`scanf_s`解析連結器會尋找名為 MOD1.obj 內的程式庫中使用的定義。

1. 中的參考，MOD2.obj`myline`和`mycircle`解決 MYGRAPH.lib 中使用的定義。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)