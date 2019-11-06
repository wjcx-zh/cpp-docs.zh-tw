---
title: C++Visual Studio 2015 和 Visual Studio 2019 之間的二進位相容性
ms.date: 10/17/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 761f6187a8b30ecb4214821c7f91d1b26e9c647c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627027"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Visual Studio 2015 和 Visual Studio 2019 之間的二進位相容性

在 Visual Studio 2013 及更舊版本中，使用不同版本的編譯器工具組和執行階段程式庫在目的檔 (OBJ)、靜態程式庫 (LIB)、動態程式庫 (DLL) 和可執行檔 (EXE) 之間所建立的二進位相容性不受保證。 

在 Visual Studio 2015 及更新版本中，C++ 工具組的主要版本號碼為 14 (Visual Studio 2015 為 v140、Visual Studio 2017 為 v141、Visual Studio 2019 為 v142)。 這反映出執行時間程式庫和使用這些編譯器版本編譯的應用程式都是二進位相容的事實。 這表示若有協力廠商程式庫是使用 Visual Studio 2015 建置，您不需要重新編譯它即可從使用 Visual Studio 2017 或 Visual Studio 2019 建置的應用程式取用它。

此規則唯一的例外，是使用 `/GL` 編譯器參數編譯的靜態程式庫或物件檔案非二進位相容。

當您混合使用 MSVC 工具組的不同支援版本所建立的二進位檔C++時，您的應用程式執行所在的 Visual 可轉散發套件不能比用來建立應用程式的工具組版本或其所使用的任何程式庫還舊。

## <a name="upgrade-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>將 Microsoft Visual C++可轉散發套件從 Visual Studio 2015 或2017升級至 Visual Studio 2019

因為我們已保留二進位相容性，並將適用于 Visual Studio 2015、2017和2019的C++ visual 可轉散發套件保留主要版本（14），所以您隨時都C++可以從這些版本中安裝一個 visual 可轉散發套件。 較新的版本將會覆寫已安裝的舊版。 如果您有來自 Visual Studio C++ 2015 或2017的 Visual 可轉散發套件，然後再安裝2019，則2019版本將會覆寫較舊的版本。 因為我們確保最新版本將會有所有最新的功能和 bug 修正，包括安全性修正，所以我們一律建議您升級至最新的可用版本。

同樣地，我們不允許在已有較新版本C++的電腦上安裝舊版的 Visual 可轉散發套件。 在已經有C++ 2019 的電腦上，從 Visual Studio 2015 或2017安裝 Visual 可轉散發套件時，將會導致安裝失敗。 此錯誤看起來會像這樣：

```
*0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.*.
```

這是設計的錯誤。 我們建議您保留最新的安裝。

## <a name="see-also"></a>請參閱

* [Visual C++ 變更歷程記錄](../porting/visual-cpp-change-history-2003-2015.md)
* [支援的最新C++視覺可轉散發套件下載](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
