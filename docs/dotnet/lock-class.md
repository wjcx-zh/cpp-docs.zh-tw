---
title: lock 類別
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 8876810b15a7d2736f2c8ab0ca1f4c6011918a5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547130"
---
# <a name="lock-class"></a>lock 類別

這個類別會自動採用同步存取的物件處理從多個執行緒的鎖定。  在建構時它會取得鎖定時終結該版本和鎖定。

## <a name="syntax"></a>語法

```
ref class lock;
```

## <a name="remarks"></a>備註

`lock` 只適用於 CLR 物件，且僅用於 CLR 程式碼中。

就內部而言，此鎖定類別會使用<xref:System.Threading.Monitor>來同步存取。 在同步處理，請參閱這個主題更詳細的資訊。

## <a name="requirements"></a>需求

**標頭檔** \<msclr\lock.h >

**命名空間**msclr

## <a name="see-also"></a>另請參閱

[lock](../dotnet/lock.md)<br/>
[lock 成員](../dotnet/lock-members.md)