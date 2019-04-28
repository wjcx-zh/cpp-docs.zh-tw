---
title: 編譯器錯誤 C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: eec529f43e23810843651888ef5722c5d0a0b2c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366351"
---
# <a name="compiler-error-c2567"></a>編譯器錯誤 C2567

無法開啟 'file' 中的中繼資料，檔案可能已刪除或移動

已在來源中參考的中繼資料檔案 (使用`#using`) 找不到相同的目錄中由編譯器後端處理序編譯器後端程序一樣。 請參閱[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)如需詳細資訊。

如果您使用，可能造成 C2567 **/c**上其中一個機器，然後在另一部電腦上的連結時間程式碼產生。 如需詳細資訊，請參閱 < [/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md))。

它也可能表示您的電腦已經沒有更多的記憶體。

若要更正這個錯誤，請確定中繼資料檔案是在相同的目錄位置中進行的建置程序的所有階段。