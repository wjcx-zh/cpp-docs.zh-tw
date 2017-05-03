---
title: "default 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "default_CPP"
dev_langs: 
  - "C++"
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# default 命名空間
`default` 命名空間會為 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 支援的內建類型指定範圍。  
  
## 語法  
  
```  
namespace default;  
```  
  
## Members  
 所有內建類型都會繼承下列成員。  
  
|||  
|-|-|  
|[default::\(type\_name\)::Equals 方法](../cppcx/default-type-name-equals-method.md)|判斷指定的物件是否等於目前的物件。|  
|[default::\(type\_name\)::GetHashCode 方法](../cppcx/default-type-name-gethashcode-method.md)|傳回這個執行個體的雜湊碼。|  
|[default::\(type\_name\)::GetType 方法](../cppcx/default-type-name-gettype-method.md)|傳回字串，表示目前的類型。|  
|[default::\(type\_name\)::ToString 方法](../cppcx/default-type-name-tostring-method.md)|傳回字串，表示目前的類型。|  
  
### 內建類型  
  
|名稱|描述|  
|--------|--------|  
|`char16`|表示 Unicode \(UTF\-16\) 字碼指標的 16 位元非數值。|  
|`float32`|32 位元 IEEE 754 浮點數。|  
|`float64`|64 位元 IEEE 754 浮點數。|  
|`int16`|16 位元帶正負號的整數。|  
|`int32`|32 位元帶正負號的整數。|  
|`int64`|64 位元帶正負號的整數。|  
|`int8`|8 位元帶正負號的數值。|  
|`uint16`|16 位元不帶正負號的整數。|  
|`uint32`|32 位元不帶正負號的整數。|  
|`uint64`|64 位元不帶正負號的整數。|  
|`uint8`|8 位元不帶正負號的數值。|  
  
## 需求  
 **標頭：**vccorlib.h  
  
## 請參閱  
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)