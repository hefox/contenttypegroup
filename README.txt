Concept module.

Based on the idea that some configuration is easier if content types had grouping


Example


function site_feature_contenttypegroup() {
  $rids_any = array(3);
  $rids_own = array(2,3);
  return array(

    // disabled some node form elements for those content types, enable most node permissions for admin user (3). 
   'general_posting' => array(
    'types'=>array(
      'event',
      'news',
      'partner',
      'page',
      'panel'
      ),
     'node_form_disable' => array(
        'author',
        'menu',
        'comment_settings',
        array('options','promote'),
        array('options','sticky'),
        array('options','premium'),
        'revision_information'
     ),
     'auto_permissions' => array(
      'create [type] content'=> $rids_any,
      'edit any [type] content'=> $rids_any,
      'edit own [type] content'=> $rids_any,
      'delete own [type] content'=>  $rids_any,
      'delete any [type] content'=> $rids_any,
      'edit any [type] content'=> $rids_any,
      'edit own [type] content'=> $rids_any,
     ),
   ),
    // adds create, delete own, edit own permissions for authentiz user
   'reg' => array(
    'types'=>array(
      'event',
      'news',
      ),
     'auto_permissions' => array(
      'create [type] content'=>  $rids_own,
      'delete own [type] content'=>  $rids_own,
      'edit own [type] content'=> $rids_own,
     ),
   ),
   // removes url alias for event, news, partner
   'no_url_alias' => array(
    'types'=>array(
      'event',
      'news',
      'partner',
      ),
     'node_form_disable' => array(
        'path',
     ),
   ),
  );
}
