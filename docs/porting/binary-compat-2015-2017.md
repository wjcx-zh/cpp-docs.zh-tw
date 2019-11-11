---
title: C++Visual Studio 2015 和 Visual Studio 2019 之間的二進位相容性
description: 描述二進位相容性在 Visual Studio 2015 C++ 、2017和2019中的編譯檔之間的運作方式。 一個 Microsoft Visual C++可轉散發套件適用于這三個版本。
ms.date: 11/07/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: e41c34abe25deefe100f525044faeac0b0c3054a
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912875"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>C++Visual Studio 2015 和 Visual Studio 2019 之間的二進位相容性

在 Microsoft Visual Studio 2013 和更早版本中，不保證物件檔案（Obj）、靜態程式庫（lib）、動態連結程式庫（Dll），以及使用不同版本的編譯器工具組建立的可執行檔（Exe）之間的二進位相容性和執行時間程式庫。

在 Visual Studio 2015 及更新版本中，C++ 工具組的主要版本號碼為 14 (Visual Studio 2015 為 v140、Visual Studio 2017 為 v141、Visual Studio 2019 為 v142)。 這種編號反映了執行時間程式庫和使用任何編譯器版本所編譯的應用程式都是二進位相容的事實。 因此，如果您有以 Visual Studio 2015 建立的協力廠商程式庫，則不需要重新編譯，就能從以 Visual Studio 2017 或 Visual Studio 2019 建立的應用程式使用它。

此規則唯一的例外是使用 `/GL` 編譯器參數編譯的靜態程式庫或物件檔案*不*是二進位相容。

當您混合使用 Microsoft C++ （MSVC）工具組的不同支援版本所建立的二進位檔C++時，您的應用程式執行所在的 Visual 可轉散發套件不能比用來建立應用程式的任何工具組版本或其所使用的任何程式庫還舊。

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>將 Microsoft Visual C++可轉散發套件從 Visual Studio 2015 或2017升級至 Visual Studio 2019

因為我們已保留二進位相容性，並在 Microsoft Visual C++可轉散發套件中將主要版本（14）保持相同，以用於 Visual Studio 2015、2017和2019，因此C++一次只能安裝一個版本的 Visual 可轉散發套件。 較新的版本會覆寫已安裝的舊版本。 如果您有來自 Visual Studio C++ 2015 或2017的 Visual 可轉散發套件，然後再安裝 Visual Studio 2019，2019版本會覆寫較舊的版本。 因為我們確定最新的版本具有所有最新的功能和 bug 修正（包含安全性修正），所以我們一律建議您升級至最新的可用版本。

同樣地，我們也不會讓您在已安裝較C++新版本的電腦上安裝較舊版本的 Visual 可轉散發套件。 在已有C++ 2019 版本的電腦上，從 Visual Studio 2015 或2017安裝 Visual 可轉散發套件，會觸發安裝失敗。 此錯誤與下列類似：

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

這是設計的錯誤。 我們建議您保留最新版本的安裝。

## <a name="see-also"></a>請參閱

* [Visual C++ 變更歷程記錄](../porting/visual-cpp-change-history-2003-2015.md)
* [支援的最新C++視覺可轉散發套件下載](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) 
