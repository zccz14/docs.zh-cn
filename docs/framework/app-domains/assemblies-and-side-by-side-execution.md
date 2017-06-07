---
title: "程序集和并行执行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程序集 [.NET Framework], 并行执行"
  - "并行执行 [.NET Framework]"
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 程序集和并行执行
并行执行是在同一台计算机上存储和执行应用程序或组件的多个版本的能力。  这意味着在同一台计算机上可以同时有运行时的多个版本，并且可以有使用其中某个运行时版本的应用程序和组件的多个版本。  并行执行使您能够更多地控制应用程序绑定到的组件版本和应用程序使用的运行时版本。  
  
 支持并行存储和执行同一程序集的不同版本是强命名中不可缺少的部分，这种支持内置于运行时基础结构中。  因为强名称程序集的版本号是其标识的一部分，所以运行时能够在全局程序集缓存中存储同一程序集的多个版本，并且在运行时加载这些程序集。  
  
 尽管运行时使您能够创建并行应用程序，但并行执行并不是自动进行的。  有关创建并行执行的应用程序的更多信息，请参见 [并行执行的组件的创建指南](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。  
  
## 请参阅  
 [运行时如何定位程序集](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [公共语言运行时中的程序集](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)