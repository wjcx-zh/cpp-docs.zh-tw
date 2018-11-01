---
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: 21d0baccaf74fc08bb110b0ae9f8b7dc108abd6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561566"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

CL 編譯器會自動呼叫連結，除非您指定 /c 選項。 CL 提供某些控制連結器，透過命令列選項和引數。 下表摘要說明 CL 影響連結的功能。

|CL 規格|CL 動作會影響連結|
|----------------------|---------------------------------|
|.C、.cxx、.cpp 或.def 以外的任何檔案名稱副檔名|傳遞做為輸入至連結的檔案名稱|
|*檔名*.def|將傳遞 /DEF:*filename*.def|
|/F*數目*|傳遞 /STACK:*數目*|
|/Fd*檔名*|將傳遞 /PDB:*檔名*|
|/Fe*檔名*|將傳遞 /out:*檔名*|
|/Fm*檔名*|傳遞 /MAP:*檔名*|
|/Gy|建立函式 (Comdat);可讓函式層級連結|
|/LD|將傳遞 /DLL|
|/LDd|將傳遞 /DLL|
|/link|將命令列的其餘部分傳遞至連結|
|/MD 或 /MT|將預設程式庫名稱放入.obj 檔案|
|/Mdd 或 /MTd|.Obj 檔案中將預設程式庫名稱。 定義符號 **_DEBUG**|
|/nologo|將傳遞 /NOLOGO|
|/Zd|傳遞 /DEBUG|
|/Zi 或/z7|傳遞 /DEBUG|
|/Zl|省略預設程式庫名稱，從.obj 檔案|

如需詳細資訊，請參閱[編譯器選項](../../build/reference/compiler-options.md)。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)