---
title: 排除匯入屬性
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218713"
---
# <a name="exclude-import-attribute"></a>排除匯入屬性

**C++特殊**

排除從類型程式庫標頭檔產生的項目。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***exclude (** "*Name1*" [ **,** "*Name2*" ...] **)**

### <a name="parameters"></a>參數

*Name1*\
要排除的第一個項目。

*Name2*\
選擇性要排除的第二個和更新的專案 (如有必要)。

## <a name="remarks"></a>備註

類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 這個屬性可以接受任意數目的引數, 其中每個都是要排除的最上層類型程式庫專案。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
