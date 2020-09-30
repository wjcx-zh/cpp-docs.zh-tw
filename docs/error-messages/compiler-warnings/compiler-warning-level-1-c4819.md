---
title: 編譯器警告 (層級 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: f81a4f44a489e2e4c5bd5c063d922129581819f9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509358"
---
# <a name="compiler-warning-level-1-c4819"></a>編譯器警告 (層級 1) C4819

> 檔案包含無法在目前字碼頁中表示的字元 (*數位*) 。 請以 Unicode 格式儲存檔案，以防止資料遺失。

當您使用無法表示檔案中所有字元的字碼頁在系統上編譯 ANSI 原始程式檔時，就會發生 C4819。

有幾種方法可以解決 C4819。 其中一種簡單的方式是移除有問題的字元（如果不需要的話），例如，如果它是在批註中。 您可以將主控台中的系統字碼頁設定為支援您的原始程式碼所使用字元集的字碼頁。 您可以使用 Unicode [escape 序列](../../c-language/escape-sequences.md) ，建立只在原始程式碼中使用基本 ANSI 字元集的字元或字串。 最後，您可以使用簽章的 Unicode 格式（也稱為位元組順序標記 (BOM) ）來儲存檔案。

若要以 Unicode 格式儲存檔案，請在 Visual Studio**中選擇 [** 檔案  >  **另存**新檔]。 在 [ **另存** 新檔] 對話方塊中，選取 [ **儲存** ] 按鈕上的下拉式清單，然後選擇 [ **以編碼方式儲存**]。 如果您儲存至相同的檔案名，您可能需要確認要取代該檔案。 在 [ **先進儲存選項** ] 對話方塊中，選擇可代表檔案中所有字元的編碼方式，例如， **Unicode (utf-8 （簽章) -字碼頁 65001**），然後選擇 **[確定]**。
