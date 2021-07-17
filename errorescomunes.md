# Errores Comunes

Un error común a la hora de testear bots es que estos no comprueben si pueden enviar mensajes embed al canal y la política de Discord Things exije que los bots posean un sistema Antierrores.

Osea que si un bot tiene un error a la hora de ejecutar un comando este devuelva un mensaje explicando el por que del error.

Este canal esta hecho exclusivamente para dar un mejor soporte a los desarrolladores que tengan problemas con su aplicación.

# Error de permisos

La manera de solucionar este sencillo error es comprobar los permisos que nuestro bot posea en el canal.

La mejor manera de solucionar esto es usando el método permissionsFor de la clase GuildChannel.

Ejemplo de uso:
// Discord.js v12.5.3
if(channel.permissionsFor(message.guild.me).has("EMBED_LINKS")) return message.channel.send("No puedo enviar mensajes embed por que no tengo el permiso de `Insertar Enlaces`.")

// Multiples Permisos
if(channel.permissionsFor(message.guild.me).has("EMBED_LINKS" && "USE_EXTERNAL_EMOJIS")) return message.channel.send("No puedo ejecutar el comando por que no tengo el permiso de `Insertar Enlaces` y `Usar Emojis Externos`.")

// Definir "channel"
let channel = message.channel // Si desean que sea el canal donde se envia el comando

let channel = message.mentions.channels.first() // Si es en el caso de establecer un canal

# Error de al conectar bot a un canal de voz

Para resolver este bug usaremos el sencillo resolvedor de excepciones try y su acompañante catch.

Ejemplo de uso:
// Discord.js v12.5.3
try {
  await channel.join()
} catch (e) {
  return message.channel.send("El canal de voz tiene limite de usuarios.")
}
//Ojo no necesariamente significa es que tiene limite de usuarios si no por que tampoco tiene permisos puede hacer que compruebe los permisos con el ejemplo de arriba y usar try y catch para el limite de usuarios

# Error con limite de caracteres

Otro error común en los comandos como 8ball o embed-say es el limite de caracteres que tiene un parametro embed.

La manera más fácil de solucionar este error es comprobando la longitud del texto

Ejemplo de uso:
let texto = args.join(" ")
//En caso de la descripción del embed:
if(texto.length > 2048) return message.channel.send("El texto no puede superar los 2048 caracteres.")

//En caso de un field:
if(texto.length > 1024) return message.channel.send("El texto no puede superar los 1024 caracteres.")
