---
title: 編譯器警告 (層級 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777820"
---
# <a name="compiler-warning-level-1-c4819"></a>編譯器警告 (層級 1) C4819

> 檔案包含無法在目前的字碼頁中表示的字元 (*數字*)。 請以 Unicode 格式儲存檔案，以防止資料遺失。

當您編譯 ANSI 原始程式檔使用字碼頁無法表示的檔案中的所有字元的系統上時，就會發生 C4819。

有數種方式可解決 C4819。 一個簡單方式是移除有問題的字元，如果您不需要它，比方說，如果是在註解。 您可以支援您的程式碼所使用的字元集的其中一個控制台中設定的系統字碼頁。 您可以使用 Unicode[逸出序列](/cpp/c-language/escape-sequences)建立字元或字串，使用基本的 ANSI 字元集，則為在原始程式碼中的。 最後，您也可以使用簽章，也就是將位元組順序標記 (BOM) 以 Unicode 格式儲存檔案。

若要將檔案儲存在 Unicode 格式，在 Visual Studio 中，選擇**檔案** > **另存新檔**。 在 **另存新檔**對話方塊方塊中，選取下拉式清單上**儲存**按鈕，然後選擇**使用編碼方式儲存**。 如果您將儲存到相同的檔案名稱，您可能需要確認您想要取代的檔案。 中**進階儲存選項**] 對話方塊中，選擇可以代表檔案中的所有字元編碼方式 — 比方說， **Unicode (utf-8 有簽章)-字碼頁 65001**，然後選擇 [ **確定**。