---
title: 編譯器警告 (層級 1) C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596608"
---
# <a name="compiler-warning-level-1-c4819"></a>編譯器警告 (層級 1) C4819

檔案包含無法在目前字碼頁 (數字) 中表示的字元。 請以 Unicode 格式儲存檔案，以防止資料遺失。

在字碼頁無法表示檔案中所有字元的系統上編譯 ANSI 原始程式檔時，就會發生 C4819。

若要解決 C4819，請以 Unicode 格式儲存檔案。 在 Visual Studio 中，選擇**檔案**，**進階儲存選項**。 中**進階儲存選項**對話方塊方塊中，選取可代表檔案中的所有字元的編碼方式 — 比方說，utf-8，然後選擇  **確定**。