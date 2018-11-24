<?php

namespace AppBundle\Controller;

use AppBundle\Entity\Usuario;
use Symfony\Bundle\FrameworkBundle\Controller\Controller;
use Symfony\Component\HttpFoundation\Request;
use Symfony\Component\Routing\Annotation\Route;

class DefaultController extends Controller
{
    /**
     * @Route("/", name="homepage")
     */
    public function indexAction(Request $request)
    {
        $usuario = new usuario();
        $usuario->setNombre("Anderson");
        $usuario->setApellido("Medina");
        $usuario->setEmail("andermedina91gmail.com");
        $usuario->setPassword("1234");
        $usuario->setHabilitado("true");

        $conexion = $this->getDoctrine()->getManager();
        $conexion->persist($usuario);
        $conexion->flush();
        // replace this example code with whatever you need
        return $this->render('default/index.html.twig', [
            'usuario' => "Anderson Medina"
        ]);
    }
    /**
     * @Route("/{id}", name="homepage2")
     *
     * @param Request $request
     * @param Usuario $usuario
     */
    public function ver_usuarioAction(Request $request, Usuario $usuario)

    {

        // replace this example code with whatever you need
        return $this->render('@App/Usuario/ver_usuario.html.twig',[
            "usuario" => $usuario
        ]);


    }


}
