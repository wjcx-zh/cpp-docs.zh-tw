---
title: 嚴重錯誤 C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: c4622dd4552f7bfcc822a3aab4d5783146d68ac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581853"
---
# <a name="fatal-error-c1900"></a>嚴重錯誤 C1900

> 之間發生 Il 不符 '*tool1*'version'*number1*'和'*tool2*'version'*number2*'

在編譯器的不同階段中執行的工具不符。 *number1*並*number2*檔案參考的日期。 例如，在階段 1，編譯器前端執行 (c1.dll)，而在階段 2 中，編譯器後端執行 (c2.dll)。 檔案上的日期必須相符。

若要修正這個問題，請確定所有的更新都已套用到 Visual Studio。 如果問題持續發生，請使用**程式和功能**Windows 控制台中修復或重新安裝 Visual Studio。