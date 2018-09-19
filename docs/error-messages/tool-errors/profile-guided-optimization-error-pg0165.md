---
title: 特性指引最佳化錯誤 PG0165 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084207"
---
# <a name="profile-guided-optimization-error-pg0165"></a>特性指引最佳化錯誤 PG0165

讀取 'Filename.pgd': ' 不支援的 PGD 版本 （版本不符） '。

PGD 檔案專屬於特定的編譯器工具組。 會產生這個錯誤，當您使用不同的編譯器，用於以外*Filename*.pgd。 此錯誤表示這個編譯器工具組不能使用的資料*Filename*.pgd 最佳化目前的處理序。

若要解決此問題，重新產生*Filename*.pgd 使用目前的編譯器工具組。