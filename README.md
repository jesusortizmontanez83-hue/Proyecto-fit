<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FitAura</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Arial,sans-serif;background:linear-gradient(135deg,#12001f,#3b0764,#7c3aed,#06b6d4,#14b8a6);color:#fff}header{padding:20px 40px;display:flex;justify-content:space-between;align-items:center;background:rgba(26,22,51,0.88);position:sticky;top:0}.logo{font-size:28px;font-weight:700;color:#ff5f6d}.btn{background:#ff5f6d;color:#ffffff;padding:12px 18px;border:none;border-radius:10px;font-weight:700;cursor:pointer}.hero{padding:80px 20px;text-align:center;background:linear-gradient(135deg,#ff5f6d,#7c3aed,#2563eb,#14b8a6)}h1{font-size:56px;margin:0 0 10px}.hero p{max-width:700px;margin:0 auto 25px;color:#cbd5e1;font-size:18px}.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;padding:40px}.card{background:rgba(26,22,51,0.88);padding:24px;border-radius:18px;box-shadow:0 18px 42px rgba(76,29,149,.28)}input,select{width:100%;padding:12px;margin:8px 0;border-radius:10px;border:1px solid #334155;background:#221b45;color:#fff}.result{margin-top:10px;font-weight:700;color:#ff5f6d}.footer{padding:30px;text-align:center;color:#94a3b8}
</style>
</head>
<body>
<header><div class='logo'>FitAura</div><button class='btn' onclick='abrirPago()'>Premium 1 mes gratis</button></header>
<section class='hero'>
<h1>Transforma tu cuerpo</h1>
<p>Dietas inteligentes, cálculo de grasa corporal, seguimiento de progreso y coaches profesionales en una sola app.</p>
<button class='btn'>Empezar Gratis</button>
</section>
<section class='grid'>
<div class='card'>
<h2>Planes</h2>
<p><strong>Free:</strong> Calculadora IMC, dietas básicas y acceso limitado.</p>
<p><strong>Premium Mensual:</strong> 1 mes gratis, luego S/19.90 mensual con recetas completas, coaches y seguimiento.</p>
<p><strong>Premium Anual:</strong> 1 año completo por solo S/99 (ahorro especial).</p>
<button class='btn' onclick='abrirPago()'>Probar Premium</button>
</div>
<div class='card'>
<h2>Registro</h2>
<input placeholder='Correo'>
<input type='password' placeholder='Contraseña'>
<button class='btn'>Crear Cuenta</button>
</div>
<div class='card'>
<h2>Calculadora Completa: IMC + Grasa + Dieta</h2>
<input id='peso' placeholder='Peso kg'>
<input id='altura' placeholder='Altura cm'>
<select id='nivelReceta'>
<option value='simple'>Recetas Simples</option>
<option value='medio'>Recetas Medias</option>
<option value='elaborado'>Recetas Elaboradas</option>
</select>
<select id='diaPlan'>
<option value='Lunes'>Lunes</option>
<option value='Martes'>Martes</option>
<option value='Miércoles'>Miércoles</option>
<option value='Jueves'>Jueves</option>
<option value='Viernes'>Viernes</option>
<option value='Sábado'>Sábado</option>
<option value='Domingo'>Domingo</option>
</select>
<select id='objetivoFusion'>
<option value='18'>Recomposición Corporal</option>
<option value='24'>Definición</option>
<option value='32'>Aumento de Masa Muscular</option>
</select>
<button class='btn' onclick='calcIMC()'>Calcular Plan Completo</button>
<div id='imc' class='result'></div>
<div id='dietaPeso' class='result' style='font-size:14px;line-height:1.5'></div>
</div>

<div class='card'>
<h2>Escáner Grasa Corporal</h2>
<p>Sube mínimo 4 fotos: frente, espalda y ambos costados para una estimación más precisa.</p>
<label style='display:block;padding:12px;border:2px dashed #ff5f6d;border-radius:14px;margin:8px 0;background:rgba(255,255,255,.05);cursor:pointer'>📸 Foto Frontal (de pie, cuerpo completo)<input id='scanFront' type='file' accept='image/*' style='display:none' onchange='previewMulti("front")'></label>
<label style='display:block;padding:12px;border:2px dashed #ff5f6d;border-radius:14px;margin:8px 0;background:rgba(255,255,255,.05);cursor:pointer'>📸 Foto Espalda (de pie, cuerpo completo)<input id='scanBack' type='file' accept='image/*' style='display:none' onchange='previewMulti("back")'></label>
<label style='display:block;padding:12px;border:2px dashed #ff5f6d;border-radius:14px;margin:8px 0;background:rgba(255,255,255,.05);cursor:pointer'>📸 Costado Izquierdo (perfil completo)<input id='scanLeft' type='file' accept='image/*' style='display:none' onchange='previewMulti("left")'></label>
<label style='display:block;padding:12px;border:2px dashed #ff5f6d;border-radius:14px;margin:8px 0;background:rgba(255,255,255,.05);cursor:pointer'>📸 Costado Derecho (perfil completo)<input id='scanRight' type='file' accept='image/*' style='display:none' onchange='previewMulti("right")'></label>
<div style='display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:10px'>
<img id='prevfront' style='display:none;width:100%;height:140px;object-fit:cover;border-radius:12px'>
<img id='prevback' style='display:none;width:100%;height:140px;object-fit:cover;border-radius:12px'>
<img id='prevleft' style='display:none;width:100%;height:140px;object-fit:cover;border-radius:12px'>
<img id='prevright' style='display:none;width:100%;height:140px;object-fit:cover;border-radius:12px'>
</div>
<button class='btn' onclick='analizarGrasa()'>Escanear Cuerpo</button>
<div id='scanResult' class='result'></div>
</div>
<div class='card'>
<h2>Dietas & Recetas</h2>
<p>Gran repertorio fitness:</p>
<p>• Pollo teriyaki fit<br>• Pasta alta proteína<br>• Pancakes avena<br>• Bowl salmón<br>• Ensalada keto<br>• Arroz con pollo light<br>• Smoothies muscle gain<br>• Postres sin azúcar</p>
<button class='btn'>Ver Recetas</button>
</div>
<div class='card'>
<h2>Zona Coaches</h2>
<p>Publica rutinas, vende planes y gestiona alumnos premium.</p>
<p>Postúlate como coach:</p>
<input placeholder='Nombre completo'>
<input placeholder='Correo electrónico'>
<input placeholder='Número de contacto'>
<div style='margin:10px 0;padding:22px;border:2px dashed #ff5f6d;border-radius:16px;background:linear-gradient(135deg,#221b45,#1a1633);text-align:center'>
<input id='cvFile' type='file' accept='image/*,.pdf,.doc,.docx' onchange='mostrarArchivo()' style='width:100%;opacity:.9;cursor:pointer;background:transparent;border:none;margin:0'>
<div style='font-size:32px;margin:6px 0'>📄</div>
<p style='margin:6px 0;font-weight:700'>Sube tu CV profesional</p>
<p style='font-size:14px;color:#cbd5e1;margin:0'>Arrastra tu archivo aquí o haz clic para seleccionarlo</p>
<p style='font-size:12px;color:#94a3b8;margin-top:8px'>Formatos: PDF, DOC, DOCX, JPG, PNG</p><p id='archivoNombre' style='font-size:13px;color:#ff5f6d;margin-top:8px'></p>
</div>
<p>• Certificación fitness o nutrición<br>• Experiencia comprobable<br>• Redes sociales o marca personal</p>
<button class='btn' onclick='mostrarGracias()'>Únete</button>
</div>
</section>
<div id='graciasVentana' style='display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:999;align-items:center;justify-content:center'>
<div style='background:rgba(26,22,51,0.88);padding:40px;border-radius:22px;max-width:420px;width:90%;text-align:center;box-shadow:0 20px 50px rgba(0,0,0,.4)'>
<div style='font-size:56px'>🎉</div>
<h2 style='margin:10px 0;color:#ff5f6d'>Gracias por tu postulación</h2>
<p style='color:#cbd5e1'>Nuestro equipo revisará tu perfil y te contactará pronto.</p>
<button class='btn' onclick='cerrarGracias()'>Cerrar</button>
</div>
</div>
<div id='pagoVentana' style='display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:999;align-items:center;justify-content:center'>
<div style='background:rgba(26,22,51,0.96);padding:34px;border-radius:22px;max-width:430px;width:92%;text-align:center'>
<h2 style='color:#ff5f6d'>Activa Premium</h2>
<p style='color:#cbd5e1'>Elige tu plan premium.</p>
<button class='btn' style='width:100%;margin:8px 0' onclick="seleccionarPlan('Mensual: 1 mes gratis, luego S/19.90')">Plan Mensual</button>
<button class='btn' style='width:100%;margin:8px 0;background:#7c3aed' onclick="seleccionarPlan('Anual: 1 año por S/99')">Plan Anual</button>
<p id='planElegido' style='color:#ff5f6d;font-weight:700'>Plan seleccionado: Mensual</p>
<input placeholder='Nombre en tarjeta'>
<input placeholder='Número de tarjeta'>
<input placeholder='MM/AA'>
<input placeholder='CVV'>
<button class='btn' onclick='confirmarPago()'>Agregar tarjeta</button>
<button class='btn' style='margin-top:10px;background:#334155' onclick='cerrarPago()'>Cerrar</button>
</div>
</div>
<div class='footer'>© 2026 FitAura - Fitness Inteligente</div>
<script>
function calcIMC(){let p=parseFloat(document.getElementById('peso').value);let a=parseFloat(document.getElementById('altura').value)/100;if(!p||!a)return;let imc=(p/(a*a)).toFixed(1);let kcalBase=Math.round((22*p)+(6*(a*100))); let kcal=kcalBase;document.getElementById('imc').innerText='Tu IMC: '+imc;let tipo=document.getElementById('nivelReceta').value;let objetivo=parseInt(document.getElementById('objetivoFusion').value);let recetas='';if(tipo==='simple'){recetasDef='• Avena con berries<br>• Wrap de pollo<br>• Yogurt griego<br>• Ensalada tuna';recetasVol='• Tostadas mantequilla maní<br>• Arroz con pollo<br>• Batido banana avena<br>• Pasta carne magra';recetasReco='• Omelette fit<br>• Yogurt avena<br>• Ensalada pollo<br>• Atún arroz';}else if(tipo==='medio'){recetasDef='• Quinoa chicken bowl<br>• Pavo con camote<br>• Smoothie protein<br>• Tacos light';recetasVol='• Burrito doble proteína<br>• Pasta fit grande<br>• Hamburguesa casera<br>• Bowl teriyaki';recetasReco='• Pasta fit<br>• Bowl teriyaki<br>• Burrito saludable<br>• Hamburguesa light';}else{recetasDef='• Salmón espárragos<br>• Risotto light<br>• Sushi lean<br>• Steak ensalada';recetasVol='• Lasaña proteica<br>• Sushi premium extra arroz<br>• Steak con papas<br>• Risotto gain';recetasReco='• Salmón quinoa<br>• Sushi fit<br>• Risotto proteico<br>• Steak gourmet';}let plan='';if(objetivo<=18){kcal=Math.round(kcalBase);recetas=recetasReco;plan='Objetivo: Recomposición corporal. Calorías de mantenimiento con proteína alta.<br>';}else if(objetivo<=24){kcal=Math.round(kcalBase-450);recetas=recetasDef;plan='Objetivo: Definición. Déficit calórico para perder grasa.<br>';}else{kcal=Math.round(kcalBase+550);recetas=recetasVol;plan='Objetivo: Aumento de masa muscular. Superávit limpio para crecer.<br>';}let prote=Math.round((kcal*0.30)/4);let carb=Math.round((kcal*0.40)/4);let grasa=Math.round((kcal*0.30)/9);let dia=document.getElementById('diaPlan').value;document.getElementById('imc').innerText='Tu IMC: '+imc+' | '+dia+' | Calorías sugeridas: '+kcal+' kcal | Proteína: '+prote+'g | Carbos: '+carb+'g | Grasas: '+grasa+'g';let extraDia = dia==='Lunes'?'• Pancakes proteína<br>• Café light':dia==='Martes'?'• Tostadas fit<br>• Smoothie verde':dia==='Miércoles'?'• Avena nocturna<br>• Huevos revueltos':dia==='Jueves'?'• Yogurt bowl<br>• Fruta fresca':dia==='Viernes'?'• French toast fit<br>• Shake proteína':dia==='Sábado'?'• Waffles avena<br>• Omelette deluxe':'• Bagel integral<br>• Smoothie berries';document.getElementById('dietaPeso').innerHTML=plan+'<strong>Plan basado en Densidad Nutricional</strong><br>Prioriza alimentos altos en nutrientes y saciedad.<br><br><strong>Calorías diarias sugeridas:</strong> '+kcal+' kcal<br><strong>Macronutrientes:</strong> Proteína '+prote+'g | Carbos '+carb+'g | Grasas '+grasa+'g<br><br><strong>Día seleccionado:</strong> '+dia+'<br><br><strong>Desayuno:</strong><br>'+extraDia+'<br><em>'+Math.round(kcal*0.25)+' kcal | P '+Math.round(prote*0.25)+'g | C '+Math.round(carb*0.25)+'g | G '+Math.round(grasa*0.25)+'g</em><br>'+(objetivo<=18?'• Huevos con avena<br>• Yogurt con fruta':'')+(objetivo>18&&objetivo<=24?'• Omelette claras<br>• Avena con berries':'')+(objetivo>24?'• Tostadas con mantequilla maní<br>• Batido banana proteína':'')+'<br><strong>Almuerzo:</strong><br><em>'+Math.round(kcal*0.35)+' kcal | P '+Math.round(prote*0.35)+'g | C '+Math.round(carb*0.35)+'g | G '+Math.round(grasa*0.35)+'g</em><br>'+(objetivo<=18?'• Pollo con arroz integral<br>• Bowl balanceado':'')+(objetivo>18&&objetivo<=24?'• Pavo con quinoa<br>• Ensalada chicken bowl':'')+(objetivo>24?'• Carne magra con arroz<br>• Pasta con pollo':'')+'<br><strong>Snacks:</strong><br><em>'+Math.round(kcal*0.15)+' kcal | P '+Math.round(prote*0.15)+'g | C '+Math.round(carb*0.15)+'g | G '+Math.round(grasa*0.15)+'g</em><br>'+(objetivo<=18?'• Frutos secos<br>• Yogurt griego':'')+(objetivo>18&&objetivo<=24?'• Manzana con yogurt<br>• Protein shake light':'')+(objetivo>24?'• Sandwich pavo<br>• Batido avena':'')+'<br><strong>Cena:</strong><br><em>'+Math.round(kcal*0.25)+' kcal | P '+Math.round(prote*0.25)+'g | C '+Math.round(carb*0.25)+'g | G '+Math.round(grasa*0.25)+'g</em><br>'+(objetivo<=18?'• Salmón con verduras<br>• Wrap fit':'')+(objetivo>18&&objetivo<=24?'• Pescado con ensalada<br>• Tortilla verduras':'')+(objetivo>24?'• Pollo con papas<br>• Burrito proteína':'')+'<br><br><strong>Recetas '+tipo+':</strong><br>'+recetas;}
function dieta(){let n=parseInt(document.getElementById('nivel').value);let tipo=document.getElementById('nivelReceta')?document.getElementById('nivelReceta').value:'simple';let recetas='';if(tipo==='simple'){recetas=' Omelette fit, Ensalada pollo, Yogurt avena';}else if(tipo==='medio'){recetas=' Pasta fit, Bowl teriyaki, Burrito saludable';}else{recetas=' Salmón quinoa, Risotto proteico, Sushi fit';}let t='';if(n<=18)t='Plan recomposición: proteína alta + carbo moderado. Recetas:'+recetas;else if(n<=24)t='Plan definición: déficit calórico + cardio + fuerza. Recetas:'+recetas;else t='Plan volumen limpio: superávit controlado + proteína alta. Recetas:'+recetas;document.getElementById('dieta').innerText=t;}
function mostrarGracias(){document.getElementById('graciasVentana').style.display='flex';}
function cerrarGracias(){document.getElementById('graciasVentana').style.display='none';}
function mostrarArchivo(){let file=document.getElementById('cvFile').files[0];if(file){document.getElementById('archivoNombre').innerText='Archivo seleccionado: '+file.name;}}
function abrirPago(){document.getElementById('pagoVentana').style.display='flex';}
function cerrarPago(){document.getElementById('pagoVentana').style.display='none';}
let planActual='Mensual: 1 mes gratis, luego S/19.90';
function seleccionarPlan(plan){planActual=plan;document.getElementById('planElegido').innerText='Plan seleccionado: '+plan;}
function confirmarPago(){alert('Tarjeta agregada. Activaste el plan '+planActual);cerrarPago();}
function previewScan(){}
function previewMulti(side){let input=document.getElementById('scan'+side.charAt(0).toUpperCase()+side.slice(1));let file=input.files[0];if(!file)return;let img=document.getElementById('prev'+side);img.src=URL.createObjectURL(file);img.style.display='block';}
function analizarGrasa(){let req=['scanFront','scanBack','scanLeft','scanRight'];for(let id of req){if(!document.getElementById(id).files[0]){document.getElementById('scanResult').innerHTML='Faltan fotos: frente, espalda y ambos costados.';return;}}let peso=parseFloat(document.getElementById('peso').value)||70;let altura=parseFloat(document.getElementById('altura').value)||170;let imc=peso/Math.pow(altura/100,2);let grasa=Math.round((1.15*imc)+(0.23*25)-12);let tipo='';let parecido='';if(grasa<10){tipo='Atlético';parecido='Definido y cintura estrecha';}else if(grasa<18){tipo='Fitness';parecido='Marcado moderado y balanceado';}else if(grasa<25){tipo='Promedio';parecido='Composición estándar';}else{tipo='Elevado';parecido='Mayor grasa abdominal';}document.getElementById('scanResult').innerHTML='Análisis 4 ángulos completado ✔<br>Grasa estimada: '+grasa+'%<br>Tipo corporal: '+tipo+'<br>Más parecido a: '+parecido;}
</script>
</body>
</html>
