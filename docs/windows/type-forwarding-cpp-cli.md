---
title: 類型轉送 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 627b0a881795a963e3739accc351ee684b7b8232
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644930"
---
# <a name="type-forwarding-ccli"></a>類型轉送 (C++/CLI)
*類型轉送*可讓您將類型移一個組件 （A） 從另一個組件 （組件 B），使得您不需要重新編譯使用組件 a 的用戶端  
  
## <a name="all-platforms"></a>所有平台  
 在 所有執行階段不支援此功能。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 在 Windows 執行階段不支援此功能。  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/ZW`  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 下列程式碼範例示範如何使用類型轉送。  
  
### <a name="syntax"></a>語法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>參數  
 *new*  
 組件，其中您要移動的類型定義。  
  
 *type*  
 型別定義您要移動到另一個組件。  
  
### <a name="remarks"></a>備註  
 隨附的元件 （組件），並是之後要用戶端應用程式，您可以使用類型轉送將類型從元件 （組件） 移到另一個組件，隨附於更新的元件 （和任何所需的其他組件） 和用戶端應用程式仍然可以運作而不需要重新編譯。  
  
 類型轉送僅適用於現有的應用程式所參考的元件。 當您重建應用程式時，必須有適當的組件參考的任何應用程式中使用的類型。  
  
 當從組件轉送型別 （類型 A），您必須新增`TypeForwardedTo`該型別，以及組件參考的屬性。 您所參考的組件必須包含下列其中一項：  
  
-   類型 a 定義  
  
-   A`TypeForwardedTo`型別 A，以及組件參考的屬性。  
  
 轉送的類型的範例包括：  
  
-   ref 類別  
  
-   實值類別  
  
-   列舉  
  
-   介面  
  
 您無法轉送下列類型：  
  
-   泛型類型  
  
-   原生類型  
  
-   巢狀型別 （如果您想要轉寄的巢狀的類型，您應該轉送封入類型）  
  
 您可以將類型轉送至組件中任何以 common language runtime 為目標的語言撰寫。  
  
 因此，如果用來建置組件 A.dll 原始程式碼檔案包含的類型定義 (`ref class MyClass`)，並想要將該類型移至組件 B.dll 的定義，您會：  
  
1.  移動`MyClass`類型定義用來建置 B.dll 原始程式碼檔案。  
  
2.  建置組件 B.dll  
  
3.  刪除`MyClass`類型從原始程式檔用來建置 A.dll，並將它取代為下列定義：  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  建置組件 A.dll。  
  
5.  您可以使用 A.dll 不需要重新編譯用戶端應用程式。  
  
### <a name="requirements"></a>需求  
 編譯器選項：`/clr`