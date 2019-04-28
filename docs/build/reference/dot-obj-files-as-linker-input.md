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
ms.openlocfilehash: c55c3181c2ddfabddce882a473e56d952a7e5d81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293273"
---
# <a name="obj-files-as-linker-input"></a>.Obj 檔做為連結器輸入

連結器工具 （連結。EXE) 接受通用物件檔案格式 (COFF) 的.obj 檔案。

## <a name="remarks"></a>備註

Microsoft 提供通用物件檔案格式的完整的描述。 如需詳細資訊，請參閱 < [PE 格式](/windows/desktop/Debug/pe-format)。

## <a name="unicode-support"></a>Unicode 支援

從 Visual Studio 2005 開始，Microsoft MSVC 編譯器支援 Unicode 字元在識別項中所定義的 ISO/IEC C 和C++標準。 舊版編譯器支援只能使用 ASCII 字元在識別項。 若要支援 Unicode 名稱中的函式、 類別和靜態變數，編譯器和連結器使用 COFF 符號.obj 檔中的 Unicode utf-8 編碼方式。 Utf-8 編碼是向上相容於舊版的 Visual Studio 所使用的 ASCII 編碼。

如需有關編譯器和連結器的詳細資訊，請參閱[編譯器和連結器中的 Unicode 支援](unicode-support-in-the-compiler-and-linker.md)。 如需 Unicode 標準的詳細資訊，請參閱[Unicode](http://www.unicode.org/)組織。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](link-input-files.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[Unicode 的支援](../../text/support-for-unicode.md)<br/>
[編譯器和連結器中的 Unicode 支援](unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode 標準](http://www.unicode.org/)<br/>
[PE 格式](/windows/desktop/Debug/pe-format)
