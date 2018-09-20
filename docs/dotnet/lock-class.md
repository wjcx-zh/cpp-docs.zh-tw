---
title: lock 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380291"
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