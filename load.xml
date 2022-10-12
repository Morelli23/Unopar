<?php
$birth_date = $_REQUEST["birth_date"];
$ano = explode('-', $birth_date)[0];
$birth_date = new DateTime($birth_date);

// Transformando arquivo XML em Objeto
$xml = simplexml_load_file('signos.xml');

function compare($data, $test1, $test2){
	if($data >= $test1 && $data <= $test2)
		return true;
	return false;
}

function dateToUs($date)
{
	return new DateTime(date('Y-m-d', strtotime(str_replace("/","-",$date))));
}

function xmlobject2array($xml)
{ 
    return json_decode(json_encode($xml), TRUE);
}

foreach($xml->signo as $signo){
	$signo = xmlobject2array($signo);
	$di = dateToUs($signo['dataInicio'].'/'.$ano);
	$df = dateToUs($signo['dataFim'].'/'.$ano);
	$seu_signo = $signo['signoNome'];
	if(compare($birth_date, $di, $df))
		break;
};

print_r(strtolower($seu_signo));
exit();
