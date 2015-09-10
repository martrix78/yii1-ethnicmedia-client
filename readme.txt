=== EthnicMedia ===
Contributors: EthnicMedia,
Tags: EthnicMedia, Ad, classifield
Requires at least: 3.2
Tested up to: 4.2.3
Stable tag: 4.2.3
License: GPLv2 or later



== Description ==
System allows you to receive private messages and display them on your site.
To obtain API key to register http://core.ethnicmedia.us


== Installation ==

1. Upload the  plugin to your extension directory,
2. add to config.php
 	'aliases' => array(
		'emclient'  => dirname(__FILE__) . '/../extensions/' ,
	),
3. Add to params
	'EM_apiKey' => API KEY,

4. Add to SiteController.php

	public function actions(){
		return array(
		'emclient' => array(
			'class'    => 'emclient.EmclientAction',
			'debug'    => true,
			'lang'     => 'en',
			'adsLimit' => 20,

		  ),
		);
	}

	public function actionClassifield(){
		$categoryId=Yii::app()->request->getParam('categoryId');
		$page=Yii::app()->request->getParam('page');
		$this->render('ad',array('categoryId'=>$categoryId,'page'=>$page));
	}

example of use on  template (ad.php):

<div id="EM_ad_form"  class="adform">
	<?php $this->widget('emclient.Emformwidget',array('adId'=>5))?>
</div>
<div class="ad">
	<?php $this->widget('emclient.Emadsdisplaywidget',array('categoryId'=>$categoryId,'page'=>$page))?>
</div>


== Changelog ==

