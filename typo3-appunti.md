

## Docker
* [Installing Docker Toolbox for TYPO3 CMS on Window 10 Home](https://youtu.be/6Q0-wlNNK3I)

## Custom content elements
* [Custom content elements made easy - EXT: mask](https://typo3worx.eu/2016/11/typo3-custom-content-elements-made-easy/)
  Mask is different from all solutions because it uses only native core functions. If you export the custom content elements with the extension „Mask exporter“ and install the result, you can throw away „mask“ and „mask_exporter“ and your custom content elements run smoothly just with the TYPO3 core!  Furthermore it provides a nice backend module to create the custom content elements via drag and drop.
Custom content elements are just one part. Additionally you can enrich backend layouts with content elements / fields.
* [Custom Content Elements - best practise](https://www.slideshare.net/cpsitgmbh/cce-custom-content-elements-best-practice)  
  how to configure and set up custom content elements using mask and mask_export. You will learn about best practice in storing your  configuration and templates in an own extension. You get an overview of all the feature the mask_export extension offers and what is the best way to customize even the export content.
* [Mask export](https://packagist.org/packages/ichhabrecht/mask-export)
  Mask offers an easy way to create content elements but has some disadvantage when you need to take care about performance. Especially the frontend rendering can take at lot of time for uncached pages. Instead of relying on TYPO3 CMS core rendering, all elements are rendered by an own Extbase Controller. As this was needed to support former version of TYPO3 CMS, it was deprecated with the introduction of fluid_styled_content and the concepts of DataProcessors in TYPO 7 LTS.
This is what mask_export is developed for. It takes the content element information from the mask configuration and generates the needed code to get those elements to work with pure TYPO3 CMS core functionality out of the box. It bundles all necessary information into an own extension that can be installed and used in every other TYPO3 CMS system.
* [Mask Video (only in German)](https://jweiland.net/video-anleitungen/typo3/interessante-typo3-extensions/mask.html)

