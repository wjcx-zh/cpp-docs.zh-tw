---
title: C++ 二進位相容性 2015-2019
description: 描述二進位相容性在 Visual Studio 2015 C++ 、2017和2019中的編譯檔之間的運作方式。 一個 Microsoft Visual C++可轉散發套件適用于這三個版本。
ms.date: 11/18/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: b729cdcc4a494e60ec58314fe23b02c1816e8412
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188781"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-2017-and-2019"></a>C++Visual Studio 2015、2017和2019之間的二進位相容性

Visual Studio 2013 和C++較早版本中的 Microsoft （MSVC）編譯器工具組不保證版本之間的二進位相容性。 您無法連結化物件檔案、靜態程式庫、動態連結程式庫，以及由不同版本所建立的可執行檔。 Abi、物件格式和執行時間程式庫不相容。

我們已在 Visual Studio 2015、2017和2019中變更此行為。 這些編譯器的任何版本所編譯的執行時間程式庫和應用程式都是二進位相容的。 它會反映在C++工具組的主要編號中，這是所有三個版本的14個。 （工具組版本是 v140，適用于 Visual Studio 2015、v141 （2017）和適用于 v142 （2019）。 假設您有 Visual Studio 2015 建立的協力廠商程式庫。 您仍然可以在 Visual Studio 2017 或2019所建立的應用程式中使用它們。 不需要使用相符的工具組重新編譯。 最新版的 Microsoft Visual C++可轉散發套件（可轉散發套件）適用于所有版本。

二進位相容性有三個重要的限制：

- 您可以混合使用不同版本的工具組所建立的二進位檔。 不過，您必須至少使用最新的工具組來連結您的應用程式。 以下是範例：您可以將使用2017工具組所編譯的應用程式連結至使用2019編譯的靜態程式庫（如果它們是使用2019工具組所連結）。

- 您的應用程式所使用的可轉散發套件具有類似的二進位相容性限制。 當您混合使用不同支援版本的工具組所建立的二進位檔時，可轉散發版本至少必須與任何應用程式元件所用的最新工具組一樣新。

- 使用[/gl （整個程式優化）](../build/reference/gl-whole-program-optimization.md)編譯器參數編譯的靜態程式庫或物件檔案，在不同的版本之間*不*會有二進位相容性。 使用 `/GL` 編譯的所有目的檔和程式庫，都必須使用完全相同的工具組來進行編譯和最終的連結。

## <a name="upgrade-the-microsoft-visual-c-redistributable-from-visual-studio-2015-or-2017-to-visual-studio-2019"></a>將 Microsoft Visual C++可轉散發套件從 Visual Studio 2015 或2017升級至 Visual Studio 2019

我們已將 Microsoft Visual C++可轉散發套件的主要版本號碼，保留為 Visual Studio 2015、2017和2019。 這表示一次只能安裝一個可轉散發套件的實例。 較新的版本會覆寫已安裝的任何舊版本。 例如，一個應用程式可能會從 Visual Studio 2015 安裝可轉散發套件。 然後，另一個應用程式會從 Visual Studio 2019 安裝可轉散發套件。 2019版本會覆寫較舊的版本，但因為它們是二進位相容，所以先前的應用程式仍然可以正常運作。 我們確保最新版本的可轉散發套件具有所有最新的功能、安全性更新和 bug 修正。 這就是為什麼我們一律建議您升級至最新的可用版本。

同樣地，當已安裝較新版本時，您無法安裝較舊的可轉散發套件。 如果您嘗試，安裝程式會報告錯誤。 如果您在已有2019版本的電腦上安裝2015或2017可轉散發套件，您會看到類似下面的錯誤：

```Output
0x80070666 - Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
```

這是設計的錯誤。 我們建議您保留最新版本的安裝。 請確定您的安裝程式可以無訊息地從這個錯誤復原。

## <a name="see-also"></a>另請參閱

[視覺C++效果變更歷程記錄](../porting/visual-cpp-change-history-2003-2015.md)\
[支援的最新C++視覺可轉散發套件下載](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
