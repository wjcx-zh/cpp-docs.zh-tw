---
title: 特性指引最佳化錯誤 PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434514"
---
# <a name="profile-guided-optimization-error-pg0165"></a>特性指引最佳化錯誤 PG0165

讀取 'Filename.pgd': ' 不支援的 PGD 版本 （版本不符） '。

PGD 檔案專屬於特定的編譯器工具組。 會產生這個錯誤，當您使用不同的編譯器，用於以外*Filename*.pgd。 此錯誤表示這個編譯器工具組不能使用的資料*Filename*.pgd 最佳化目前的處理序。

若要解決此問題，重新產生*Filename*.pgd 使用目前的編譯器工具組。