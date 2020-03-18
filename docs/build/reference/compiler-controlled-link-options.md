---
title: 編譯器控制的 LINK 選項
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440104"
---
# <a name="compiler-controlled-link-options"></a>編譯器控制的 LINK 選項

除非您指定/c 選項，否則 CL 編譯器會自動呼叫連結。 CL 透過命令列選項和引數，提供連結器的一些控制權。 下表摘要說明 CL 中會影響連結的功能。

|CL 規格|影響連結的 CL 動作|
|----------------------|---------------------------------|
|除了 .c、.cxx、.cpp 或 .def 以外的任何副檔名|傳遞檔案名做為連結的輸入|
|*檔案名*.def|傳遞/DEF：*filename*.def|
|/F*數位*|傳遞/STACK：*number*|
|/Fd*檔案名*|傳遞/PDB：*filename*|
|/Fe*filename*|傳遞/OUT：*filename*|
|/Fm*filename*|傳遞/MAP：*filename*|
|/Gy|建立封裝函式（Comdat）;啟用函式層級連結|
|/LD|傳遞/DLL|
|/LDd|傳遞/DLL|
|/link|將其餘的命令列傳遞至連結|
|/MD 或/MT|將預設程式庫名稱放在 .obj 檔案中|
|/MDd 或/MTd|將預設程式庫名稱放在 .obj 檔案中。 定義符號 **_DEBUG**|
|/nologo|傳遞/NOLOGO|
|/Zd|傳遞/DEBUG|
|/Zi 或/Z7|傳遞/DEBUG|
|/Zl|從 .obj 檔案省略預設程式庫名稱|

如需詳細資訊，請參閱[MSVC 編譯器選項](compiler-options.md)。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
