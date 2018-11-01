---
title: 編譯器錯誤 C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490270"
---
# <a name="compiler-error-c3859"></a>編譯器錯誤 C3859

超出 PCH 的虛擬記憶體範圍；請使用等於或大於 '-Zmvalue' 的命令列選項重新編譯

先行編譯標頭檔對編譯器正在嘗試放入其中的資料量而言太小。 使用 **/Zm**編譯器旗標，指定較大的值，為先行編譯標頭檔。 如需詳細資訊，請參閱 < [/Zm （指定先行編譯標頭記憶體配置上限）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。