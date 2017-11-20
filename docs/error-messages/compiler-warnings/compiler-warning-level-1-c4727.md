---
title: "編譯器警告 （層級 1） C4727 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4727
dev_langs: C++
helpviewer_keywords: C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15a8a74fc4c15e507fc8a651e9849fc82e3b9c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4727"></a>編譯器警告 (層級 1) C4727
"的 PCH 具名 pch_file obj_file_1 和 obj_file_2 中找到相同的時間戳記。  使用第一個 PCH。  
  
 編譯多個與編譯時，就會發生 C4727 **/Yc**，而且編譯器無法將所有的.obj 檔案，具有相同的.pch 時間戳記標示。  
  
 若要解決，編譯某個原始程式檔與**/Yc /c** （建立 pch），然後其他人使用分開編譯**/Yu /c** （使用 pch），然後將它們連結在一起。  
  
 因此，如果您執行下列動作，會產生 C4727:  
  
 **cl /clr /GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 您會執行下列改為：  
  
 **cl /clr /GL a.cpp /Ycstdafx.h /c**  
  
 **cl /clr /GL b.cpp c.cpp /Yustdafx.h /link a.obj**  
  
 如需詳細資訊，請參閱  
  
-   [/Yc （建立先行編譯標頭檔）](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu （使用先行編譯標頭檔）](../../build/reference/yu-use-precompiled-header-file.md)