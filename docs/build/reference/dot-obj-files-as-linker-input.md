---
title: .Obj 檔做為連結器輸入
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 3e02ccc09ae8c9c2f3df88bc1767ff0188baa1f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492944"
---
# <a name="obj-files-as-linker-input"></a>.Obj 檔做為連結器輸入

連結器工具 (連結)。EXE) 接受通用物件檔案格式 (COFF) 中的 .obj 檔案。

## <a name="remarks"></a>備註

Microsoft 提供通用物件檔案格式的完整描述。 如需詳細資訊, 請參閱[PE 格式](/windows/win32/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支援

從 Visual Studio 2005 開始, Microsoft MSVC 編譯器支援識別碼中的 Unicode 字元, 如 ISO/IEC C 和C++標準所定義。 舊版編譯器僅支援識別碼中的 ASCII 字元。 為了支援函式、類別和靜態的名稱中的 Unicode, 編譯器和連結器會針對 .obj 檔案中的 COFF 符號使用 Unicode UTF-8 編碼。 UTF-8 編碼的向上與舊版 Visual Studio 所使用的 ASCII 編碼相容。

如需編譯器和連結器的詳細資訊, 請參閱[編譯器和連結器中的 Unicode 支援](unicode-support-in-the-compiler-and-linker.md)。 如需 Unicode 標準的詳細資訊, 請參閱[unicode](https://www.unicode.org/)組織。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](link-input-files.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[Unicode 的支援](../../text/support-for-unicode.md)<br/>
[編譯器和連結器中的 Unicode 支援](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 標準](https://www.unicode.org/)<br/>
[PE 格式](/windows/win32/Debug/pe-format)
