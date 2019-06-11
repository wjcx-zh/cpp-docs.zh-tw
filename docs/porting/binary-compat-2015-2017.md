---
title: Visual Studio 2015 和 Visual Studio 2019 之間的 C++ 二進位相容性
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449044"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Visual Studio 2015 和 Visual Studio 2019 之間的 C++ 二進位相容性

在 Visual Studio 2013 及更舊版本中，使用不同版本的編譯器工具組和執行階段程式庫在目的檔 (OBJ)、靜態程式庫 (LIB)、動態程式庫 (DLL) 和可執行檔 (EXE) 之間所建立的二進位相容性不受保證。 

在 Visual Studio 2015 及更新版本中，C++ 工具組的主要版本號碼為 14 (Visual Studio 2015 為 v140、Visual Studio 2017 為 v141、Visual Studio 2019 為 v142)。 這反映以任一編譯器版本編譯的執行階段程式庫和應用程式為二進位相容。 這表示若有協力廠商程式庫是使用 Visual Studio 2015 建置，您不需要重新編譯它即可從使用 Visual Studio 2017 或 Visual Studio 2019 建置的應用程式取用它。

此規則唯一的例外，是使用 `/GL` 編譯器參數編譯的靜態程式庫或物件檔案非二進位相容。 

當您混合以 MSVC 工具組不同支援版本所建置的二進位檔時，您應用程式執行所在的 Visual C++ 可轉散發套件不能比用來建置應用程式之任何工具組版本或它使用的任何程式庫舊。 

## <a name="see-also"></a>另請參閱

[Visual C++ 變更歷程記錄](../porting/visual-cpp-change-history-2003-2015.md)
