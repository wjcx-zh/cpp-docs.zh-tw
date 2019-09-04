---
title: inject_statement 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220988"
---
# <a name="inject_statement-import-attribute"></a>inject_statement 匯入屬性

**C++特殊**

將其做為來源文字的引數插入至類型程式庫標題。

## <a name="syntax"></a>語法

> **#import***類型-程式庫***inject_statement (** "*source-text*" **)**

### <a name="parameters"></a>參數

*來源-文字*\
要插入至類型程式庫標題檔案的來源文字。

## <a name="remarks"></a>備註

文字會放在命名空間宣告的開頭, 以包裝標頭檔中的*型別程式庫*內容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
