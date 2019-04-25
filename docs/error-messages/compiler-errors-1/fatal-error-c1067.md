---
title: 嚴重錯誤 C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165849"
---
# <a name="fatal-error-c1067"></a>嚴重錯誤 C1067

編譯器限制：已超過類型記錄的大小的 64k 限制

如果符號己超過 247 個字元的裝飾的名稱，就可能發生這個錯誤。  若要解決，請縮短符號名稱。

當編譯器產生偵錯資訊時，它就會發出型別記錄，來定義在原始程式碼中遇到的型別。  例如，型別記錄包括簡單的結構和函式引數清單。  這些類型的記錄部分可以是大型清單。

沒有任何類型的記錄大小的 64k 限制。  如果超出該的 64k 限制會發生此錯誤。

如果有許多的符號名稱太長，或有太多成員的類別、 結構或等位，也會發生 C1067。