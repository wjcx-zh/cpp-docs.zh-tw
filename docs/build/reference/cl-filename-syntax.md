---
title: CL 檔名語法
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: d2dd51370fd346c4cd7dad7bb97bfa76a9f759d9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420722"
---
# <a name="cl-filename-syntax"></a>CL 檔名語法

CL 可以接受其名稱遵循 FAT、HPFS 或 NTFS 命名慣例的檔案。 任何檔名都可以包含完整或部分路徑。 完整路徑包括磁碟機名稱和一個或多個目錄名稱。 CL 可以接受的檔名分隔的反斜線 (\\) 或正斜線 （/）。 包含空格的檔名必須以雙引號字元括起來。 部分路徑省略磁碟機名稱，CL 會假設為目前的磁碟機。 如果您不指定路徑，CL 會假設檔案是在目前的目錄。

副檔名決定檔案的處理方式。 會編譯副檔名為.c、.cxx 或 .cpp 的 C 和 C++ 檔案。 其他檔案，包括 .obj 檔案、程式庫 (.lib) 和模組定義 (.def) 檔，會不經處理即直接傳遞至連結器。

## <a name="see-also"></a>另請參閱

[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)
