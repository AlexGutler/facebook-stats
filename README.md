facebook-stats
==============

/* 
  Código simples para contabilidade de compartilhamentos, likes, comments 
  de uma página do facebook caso queira exibir algumas destas informações em seu site

  Simple code for accounting shares, likes, comments
  from facebook page if you want to display some of this information on your website
*/

<php
    $source_url = "https://www.facebook.com/your-page-here"; //This could be anything URL
     
    $url = "http://api.facebook.com/restserver.php?method=links.getStats&urls=".urlencode($source_url);
    $xml = file_get_contents($url);
    $xml = simplexml_load_string($xml);
    $shares = $xml->link_stat->share_count;
    $likes = $xml->link_stat->like_count;
    $comments = $xml->link_stat->comment_count;
    $total = $xml->link_stat->total_count;
    $max = max($shares,$likes,$comments);
?>
