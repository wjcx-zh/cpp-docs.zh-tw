---
title: LIB 輸入檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lib-input-files"></a>LIB 輸入檔
LIB 所預期的輸入的檔而定的模式，這正在使用它下, 表所示。  
  
|模式|輸入|  
|----------|-----------|  
|預設值 （建立或修改程式庫）|COFF 物件檔 (.obj)，COFF 程式庫 (.lib)，32 位元物件模型的格式 (OMF) 物件檔 (.obj)|  
|擷取具有 /EXTRACT 的成員|COFF 程式庫 (.lib)|  
|建立匯出檔案，並匯入與 /DEF 程式庫|模組定義 (.def) 檔、 COFF 物件檔 (.obj)、 COFF 程式庫 (.lib)、 32 位元 OMF 目的檔 (.obj)|  
  
> [!NOTE]
>  16 位元版本的 LIB 所建立的 OMF 程式庫不能做為輸入 32 位元版本的 LIB。  
  
## <a name="see-also"></a>另請參閱  
 [LIB 概觀](../../build/reference/overview-of-lib.md)