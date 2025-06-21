package com.nutrilens.nutrilens_backend.controller;

import org.springframework.web.bind.annotation.*;
import org.springframework.http.ResponseEntity;
import org.springframework.web.multipart.MultipartFile;
import org.springframework.http.HttpStatus;

import java.util.List;

@RestController
@RequestMapping("/api/ocr")
@CrossOrigin(origins = "http://localhost:3000")
public class OCRController {

    @PostMapping("/upload")
    public ResponseEntity<List<String>> uploadReceipt(@RequestParam("file") MultipartFile file) {
        System.out.println("File received: " + file.getOriginalFilename());

        // Mock result
        List<String> items = List.of("Doritos", "Coke", "Avocado");
        return new ResponseEntity<>(items, HttpStatus.OK);
    }
}
