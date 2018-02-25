---
title: "元件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.component
- component_CPP
dev_langs:
- C++
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3edb2f68b479eeadca777e0707dd96e148d13fe8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="component"></a>元件
從原始程式檔內部收集瀏覽資訊或相依性資訊的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## <a name="remarks"></a>備註  
  
## <a name="browser"></a>瀏覽器  
 您可以開啟或關閉收集功能，而且可以指定要在收集的資訊中忽略的特定名稱。  
  
 使用開啟或關閉來控制收集 pragma 前方的瀏覽資訊。 例如:   
  
```  
#pragma component(browser, off)  
```  
  
 讓編譯器停止收集瀏覽資訊。  
  
> [!NOTE]
>  若要開啟這個 pragma，瀏覽資訊的收集[必須先啟用瀏覽資訊](../build/reference/building-browse-information-files-overview.md)。  
  
 **參考**選項才能使用，不論*名稱*引數。 使用**參考**沒有*名稱*開啟或關閉參考的收集 （其他瀏覽資訊仍繼續收集，但是）。 例如:   
  
```  
#pragma component(browser, off, references)  
```  
  
 讓編譯器停止收集參考資訊。  
  
 使用**參考**與*名稱*和**關閉**防止參考*名稱*出現在 [瀏覽資訊] 視窗。 使用這個語法會忽略您沒有興趣的名稱和類型，並可減少瀏覽資訊檔的大小。 例如:   
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 會忽略參考**DWORD**從該點之後。 您可以開啟參考的收集`DWORD`使用上一步**上**:  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 這是唯一的方式以繼續收集參考*名稱*; 您必須明確開啟任何*名稱*已關閉。  
  
 若要避免前置處理器展開*名稱*(例如**NULL**至**0**)，其前後放置引號：  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## <a name="minimal-rebuild"></a>最少重建  
 Visual C++ 最少重建功能需要編譯器建立和儲存 C++ 類別相依性資訊，這會佔用磁碟空間。 若要節省磁碟空間，您可以使用`#pragma component( minrebuild, off )`每當您不需要收集相依性資訊，比方說，不會變更的標頭檔中。 插入`#pragma component(minrebuild, on)`上一步 開啟相依性集合的不可變類別之後。  
  
## <a name="reduce-type-information"></a>減少類型資訊  
 **Mintypeinfo**選項可以減少指定區域的偵錯資訊。 這項資訊的容量相當可觀，會影響到 .pdb 和 .obj 檔案。 您無法在 mintypeinfo 區域中偵錯類別和結構。 使用 mintypeinfo 選項可避免下列警告：  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 如需詳細資訊，請參閱[啟用最少重建](../build/reference/gm-enable-minimal-rebuild.md)(/ Gm) 編譯器選項。  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)