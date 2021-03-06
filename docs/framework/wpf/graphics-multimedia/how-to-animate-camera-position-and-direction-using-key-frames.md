---
title: 如何：使用关键帧对照相机位置和方向进行动画处理
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 5be14513755c3b5c80c13cbc5cae889cc4663cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558824"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>如何：使用关键帧对照相机位置和方向进行动画处理
在下面的示例中，<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>用于进行动画处理的位置<xref:System.Windows.Media.Media3D.PerspectiveCamera>三维场景中。 此外，<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>用于进行动画处理照相机指向在三维场景中的方向。 这两类动画使用若干关键帧来创建动画效果的一系列：  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> 和<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>用于创建值之间平滑、 线性内的插。  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> 和<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>用于创建突然"跳转"值 （无内插） 之间。  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> 和<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>用于创建具体取决于值之间的变量过渡<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>属性。 在下面的示例中，动画启动较慢，但是时间段结束时，呈指数方式加速。  
  
## <a name="example"></a>示例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>请参阅  
 [在 3D 场景中为照相机位置和方向设置动画效果](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [3D 图形概述](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
