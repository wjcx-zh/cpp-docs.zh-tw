---
title: "Platform:: recreateexception 方法 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Exception
dev_langs: C++
helpviewer_keywords: Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e617d85c17db3c1e3cccb64786dfe7bfcfb9b1e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException 方法
這個方法僅供內部使用，使用者程式碼並不需要。 請改用 exception:: createexception 方法。

## <a name="syntax"></a>語法

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>參數
`hr`

### <a name="property-valuereturn-value"></a>屬性值/傳回值

根據指定的 HRESULT 傳回新的 Platform::Exception^。

