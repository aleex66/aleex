using System;
using System.Diagnostics;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;

public class PlayerInputSystem : MonoBehaviour
{
    private Rigidbody rb;
    private PlayerInput playerInput;
    private void Awake()
    {
        rb=GetComponent<Rigidbody>();
        playerInput=GetComponent<PlayerInput>();
        playerInput.onActionTriggered+=PlayerInput_onActionTriggered;
    }
    private void PlayerInput_onActionTriggered(InputAction.CallbackContext context)
    {
        Debug.Log(context);
    }
    public void Jump(InputAction.CallbackContext context)
    {
        if(context.performed)
        {
            Debug.Log("Jump!"+context.phase);
        rb.AddForce(Vector3.up*5f, ForceMode.Impulse);
        }
    }
}
