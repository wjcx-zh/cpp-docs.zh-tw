---
title: ".Obj 檔做為連結器輸入 |Microsoft 文件"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a2896822e97bdbb5ffdf8f869e67beadc1675b7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="obj-files-as-linker-input"></a>.Obj 檔做為連結器輸入

連結器工具 （連結。EXE) 接受通用物件檔案格式 (COFF) 的.obj 檔案。

## <a name="remarks"></a>備註

Microsoft 提供通用物件檔案格式的完整的描述。 如需詳細資訊，請參閱[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)。

## <a name="unicode-support"></a>Unicode 支援

從 Visual Studio 2005 開始，Microsoft Visual c + + 編譯器支援 Unicode 字元的 ISO/IEC C 和 c + + 標準所定義的識別項。 舊版的編譯器支援 ASCII 字元在識別項。 若要支援 Unicode 支援的函式、 類別和靜態變數名稱中，編譯器和連結器使用 COFF 符號.obj 檔中的 Unicode utf-8 編碼方式。 Utf-8 編碼方式為 upwardly 相容於使用舊版 Visual Studio 的 ASCII 編碼方式。

如需編譯器和連結器的詳細資訊，請參閱[編譯器和連結器中的 Unicode 支援](../../build/reference/unicode-support-in-the-compiler-and-linker.md)。 如需 Unicode 標準的詳細資訊，請參閱[Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123)組織。

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)  
[連結器選項](../../build/reference/linker-options.md)  
[Unicode 的支援](../../text/support-for-unicode.md)  
[編譯器和連結器中的 Unicode 支援](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode 標準](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)  
