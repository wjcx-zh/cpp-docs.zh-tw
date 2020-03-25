---
title: 編譯器警告 (層級 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c9bf60e8eec0ee6416bda3323583f3e056fce1a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174878"
---
# <a name="compiler-warning-level-1-c4819"></a>編譯器警告 (層級 1) C4819

> 檔案包含無法在目前字碼頁（*數位*）中表示的字元。 請以 Unicode 格式儲存檔案，以防止資料遺失。

當您使用無法代表檔案中所有字元的字碼頁，在系統上編譯 ANSI 原始程式檔時，就會發生 C4819。

有數種方式可以解決 C4819。 其中一個簡單的方法是移除不必要的字元（例如，如果您不需要的話），例如，如果它是在批註中。 您可以將 [控制台] 中的 [系統] 字碼頁設定為支援原始程式碼所使用之字元集的腳本。 您可以使用 Unicode[逸出序列](/cpp/c-language/escape-sequences)，建立只在原始程式碼中使用基本 ANSI 字元集的字元或字串。 最後，您可以使用簽章（也稱為位元組順序標記（BOM））以 Unicode 格式儲存檔案。

若要以 Unicode 格式儲存檔案，請在 Visual Studio 中 **，選擇 [** 檔案 > **另存**新檔]。 在 [**另存**新檔] 對話方塊中，選取 [**儲存**] 按鈕上的下拉式方塊，然後選擇 [**以編碼方式儲存**]。 如果您儲存到相同的檔案名，可能需要確認您想要取代該檔案。 在 [**先進儲存選項**] 對話方塊中，選擇可以代表檔案中所有字元的編碼方式，例如， **Unicode （utf-8 含簽章）-字碼頁 65001**，然後選擇 **[確定]** 。
